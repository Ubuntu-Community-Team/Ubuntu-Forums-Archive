---
title: "Extracting text string and re-formatting it?  Most likely 'sed' related"
date: 2008-07-30
forum: General Help
---

### Post by duckdown on 2008-07-30
Greetings all!

I am a novice user but had a question that I'm sure someone familiar with scripting or sed can answer for me (I have tried figuring it out on my own!  The man page is a disaster)

I have an extremely large eggdrop file, over 2000 lines, and its filled with ban masks

The format of the file looks like this

```
- *!*@*.bostream.se:+0:+1182990197:1187869158:duckdown:drone
- *!*@S01060014bfc8bf4e.wp.shawcable.net:+0:+1182991298:1186004949:duckdown:stop
- *!*@honeypot.no:+0:+1183057662:1183057662:duckdown:bye
- *!*@inet.cacdhh.org:+0:+1183090182:0:duckdown:spamming
- *!*@*fbx.proxad.net:+0:+1183139295:1187840826:duckdown:infected hosts
```

What I am trying to do, is extract the hostmask which is the " *!ident@hostname.com " portion you see in the beginning, and precede it with .+ban and add #channelname spamming to the end of it

Sorry if this sounds confusing, for example I want to turn

```

- *!identofspammer@honeypot.no:+0:+1183057662:1183057662:duckdown:bye
- *!*@inet.cacdhh.org:+0:+1183090182:0:duckdown:spamming

```

into

```

.+ban *!identofspammer@honeypot.no #channelname spamming 
.+ban *!*@inet.cacdhh.org #channelname spamming

```

I know there is some complex sed command that will do it but it is way way beyond my knowledge

Any help would be greatly appreciated because editing the file by hand would take all day!

Thanks greatly

---

### Post by justleen on 2008-07-30
```
cat file | awk -F ":" '{print ".+ban" $1 "#channelname spamming"}' 
```

cat file =>  get the contents.
awk -F ":"  =>  awk, with a : as field delimiter (your fields are seperated with : I noticed)

print => print the following
" .+ban "  => literal, thus in ""
$1 => the first field (everything before the first : )
" etc " => again, literal thus ""


edit: to dump to a file:
```
cat file | awk -F ":" '{print ".+ban" $1 "#channelname spamming"}' > outfile
```  use ">>" if you want to append to the outfile

---

### Post by justleen on 2008-07-30
for the kicks of it...with sed this time
```

 cat xx | sed -e 's/:.*.$/ #channelname spamming/' -e 's/^/\.+ban /'

```
cat the file
sed -e => the -e tells sed to do multiple actions, 2 replaces in this case
's/:.*.$/ #channelname spamming/'  => replace the first : to the end with text
's/^/\.+ban/'  replace start of each line with text.. mind the \.  a . is a special char, so i have to escape with a \


edit:  
if you want to change the actual file itself, instead of redirecting with >> you can use sed -i <file>
```
sed -i -e 's/:.*.$/ #channelname spamming/' -e 's/^/\.+ban /'  <filenametoedit> 
```

---

### Post by raptor2552 on 2008-07-30
Or
```

 awk -F "-" '{print ".+ban " $2}' input.file >output.file

```

Many ways many styles

edit eliminate cat to awk
```

awk -F ":" '{print ".+ban" $1 "#channelname spamming"}' input.file >output.file

```

---

### Post by duckdown on 2008-07-30
You guys are awesome!

Will try it now!

Thank you!

---

### Post by raptor2552 on 2008-07-30
duckdown

It may be a little late for this but.. be SURE to make a copy and save away the original.

I was thinking about your requirement for this and now realize my solution may still not be correct. The code I provided changes all lines not only those with the "spam".

Did you want to write the changed lines into the same file as the extracted records? If so copy and paste this into a terminal using your copied file as the inputfile
```

 awk 'BEGIN {FS=":"} {if(/spamm/) {print ".+ban" $1 " #channelname spamming"} else print $0;}'  inputfile >outputfile

```
This will match ALL lines containing "spamm" and change those lines to your requirements AND write all others unchanged to the same file.

---

### Post by duckdown on 2008-08-03
Hi guys

Finally got around to trying it -- and they all ALMOST work perfect except the output is like this:

```
.+ban- *!*@86.6?.* #channelname spamming
.+ban- *!*@88.14* #channelname spamming
.+ban- *!*@81.17* #channelname spamming
.+ban- *!*@213.6* #channelname spamming
```

instead of

```

.+ban *!*@86.6?.* #channelname spamming
.+ban *!*@88.14* #channelname spamming
.+ban *!*@81.17* #channelname spamming
.+ban *!*@213.6* #channelname spamming

```


There is a "dash" after the .+ban for some reason and I can't figure out how to get rid of it, but I'm sure its very simple

Thanks again all!

---

### Post by ghostdog74 on 2008-08-03
> **raptor2552 said:**
> 
```

 awk 'BEGIN {FS=":"} {if(/spamm/) {print ".+ban" $1 " #channelname spamming"} else print $0;}'  inputfile >outputfile

```

awk's "pattern" portion provides you an implicit "if" construct. therefore there's no need to use if in your example
```

awk '/spam/{ print ....}!/spam/{print }' file 

```

---

### Post by raptor2552 on 2008-08-03
Yes, ghostdog74 that's yet another way of doing it but I prefer the if; else construct and I don't see what is being saved. 

But anywho duckdown try this: if the line contains the string spamm it will strip out the "-" and print the conveted line to the file, all other lines are unchanged.

```
 awk 'BEGIN {FS=":"} {if(/spamm/) {sub("-",""); print ".+ban " $1 " #channelname spamming"} else print $0;}' datafile > outputfile
```

Get back to see if this is to your liking

---

