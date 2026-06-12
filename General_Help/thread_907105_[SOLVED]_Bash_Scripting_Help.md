---
title: "[SOLVED] Bash Scripting Help"
date: 2008-09-01
forum: General Help
---

### Post by senab on 2008-09-01
Hello,

I'm trying to create a small script that will parse 4 log files and them sum up a value in each. I've managed to get AWK to return the value out of the log files. I've then truncate the value to an int and try and increase total.

```
#!/bin/bash

#XXX: Hardcoded machine list!
machines='mqjmsdriver1 mqjmsdriver2 mqjmsdriver3 mqjmsdriver4'

total=0

for m in ${machines}
do
  awk 'BEGIN{total = 0; numberLines = 0;} /^rateR=/ {split($1, a, ",");total+=substr(a[1],7,20);numberLines+=1;} END { print total/numberLines; }' ~/tibco_results/${m}_cl$1.log | while read a
  do
    a=${a/.*}			# Truncate Float
    echo $a			# Just to check if the value is right
    let total="$total += $a"	# Add value to total
  done 
done

echo $total
```

The error I keep getting is:
```
line 24: let: total=0 += 2186: attempted assignment to non-variable (error token is "+= 2186")
```
Where the 2186 is one of the values from the files.

Any ideas? Thanks in advance :)

---

### Post by rouben on 2008-09-01
If you're trying to increment $total by $a's value, try this:

total=$((total+a))

I think bash doesn't like using += with variables... in other words total+=3 would work, but total+=a wouldn't.

---

### Post by senab on 2008-09-01
Thanks! I've managed to get it working. The reason it's wasn't was because I was using a loop to read the value from awk. After I've changed that and remove the loop and it's worked fine:

```
total=0

for m in ${machines}
do
  eval `awk 'BEGIN{total = 0; numberLines = 0;} /^rateR=/ {split($1, a, ",");total+=substr(a[1],7,20);numberLines+=1;} END { print "val="total/numberLines }' ~/logs/${m}_cl$1.log`
  val=${val/.*}
  total=$((total+val))
done

echo $total
```

---

