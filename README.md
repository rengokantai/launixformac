#### launixformac
#####7 Configuring your working
######setting command alias
```
alias h='echo "T"'
unalias h
```
######setting path
```
/usr/bin   /bin   /usr/sbin   /sbin   /usr/local/bin
```

######command prompt
```
\s currentshell
\d Mon Jan 1
\D %Y-%m-%d
\t 24  HH:MM:SS
\T 12  HH:MM:SS
\A 24 hour HH:MM
\@ am/pm
```
######logout out
```
.bash_logout
```
#####8 Unix
######search
````
grep -n a a.txt //show line number
grep -w a a.txt //only show world
grep -c a a.txt //show occurence
```
######grep multiple files
```
grep -Rh  //show only matching
grep -Rl  //show matching file
```
######grep coloring matching
```
grep --color=auto a a.txt
```
in .bashrc
```
export GREP_COLOR="34;47"   //matching color, background color.
export GREP_OPTIONS="--color-auto"
```
######Using regular expression
```
echo 'aAbB' | grep --color '[[:upper:]]'
```
######tr
```
echo 'zzzzz' | tr 'A-Za-z' 'N-ZA-Mn-za-m'
echo '1bca' | tr '1-9abc' 'x'       //translate all to x
echo '1bca' | tr 'a' 'bc'   //only translate a to b, discard c
```
import file
```
tr 'A-Z' 'a-z' <a.txt
tr ',' '\t' <a.txt >out.txt
```
######delete and squeezing
```
-d
-dc [:digit:] //delete complement
-sc [:digit:] //sqeeze complement
-ds [:digit:] [:alpha:]  //delete digit, squeeze alpha
-dsc [:digit:] [:digit:]  //delete non digit, squeeze digit
```
remove non-printable char
```
tr -dc [:print:] <in >out
```
######sed regex
```
sed 's/^/\t/g a.txt  //not working in mac  instead, press ctrl v tab
```
strip tags
```
sed -E 's/<[^<>]>//g' a.html
```

######cut
```
cut -c 1-3,4-7,9- a.txt  //get each line char 1-3 (1 based)
```

######diff, alter
```
diff -c a.txt b.txt   //show compelete files,seperately
diff -u a.txt b.txt   //show unified files
diff -q a.txt b.txt   //just show whether two files differ
diff -qs a.txt b.txt   //just show whether two files identical
diff -u a.txt b.txt |diffstat  //just show whether two files identical
```
######xargs
```
wc a.js
cat a.js |wc
cat a.js | xargs wc
cat a.js | xargs -t wc
```
show 2 items in line
```
echo 1 2 3 4 | xargs -n2
ls | xargs -n 3 echo
```
setplaceholder
```
cat a.txt | xargs -I {} echo "text: {}"
cat a.txt | grep 'A.*' | xargs -0 -n1   //show all lines start with A,ignore spaces
```
######xargs: usage example
```
find / -name "*.txt" -print0 | xargs -p -0 rm  //-p (interactive delete)
find / -name "*.txt" -print0 | xargs -p -0 rm -n1  //delete one by one
```
