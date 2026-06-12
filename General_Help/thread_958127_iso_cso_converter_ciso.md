---
title: "iso cso converter ciso"
date: 2008-10-25
forum: General Help
---

### Post by heiNey on 2008-10-25
i got ciso installed and it works fine, but i was wondering if anyone knew of a way to do a batch convert instead of just one file at a time?  maybe a script or something?  thanks!

---

### Post by geirha on 2008-10-25
Depends on the program (I haven't tried it). Is it command-line based? What do you write to convert one file?

---

### Post by doobiest on 2008-12-15
I originally wrote this script to batch convert logs to csv but it can be used for any type of batch process.   Not sure how clean it is though.  I've changed it to work with ciso and works for me.

##cat batch_conv
#!/bin/bash
#Usage  ./batch_conv DIR
c=1 #compression level

if [ $# -lt 1 ]; then #HELP
        echo; echo "Usage: ./batch_conv DIR";
        exit 0
fi

mkdir $1/output
for list in `ls *.iso`;
do
cso=${list%.*}".cso";
echo "${list} > $cso";
ciso $c ${list} $1/output/$cso;
done

#END


Or if you want something gritty that you can just paste into a terminal..

for list in `ls *.iso`; do cso=${list%.*}".cso"; ciso 1 ${list} $cso; done

---

### Post by geirha on 2008-12-15
No need to loop through the output of ls as it is both unnecessary and will break for filenames with whitespace.
```
for file in *.iso; do ciso 1 "$file" "${file/%.iso/.cso}"; done
```

---

### Post by doobiest on 2008-12-16
Ah very cool, didn't know you can do that.

---

