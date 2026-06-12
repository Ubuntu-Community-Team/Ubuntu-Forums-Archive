---
title: "Getting terminal to display in Big-Endian"
date: 2008-09-14
forum: General Help
---

### Post by imneal on 2008-09-14
Hello all, 


I'm having trouble with reading some outputs for commands on my terminal.  I'm taking an assembly class that we need to ssh into a unix server on school  to run SPIM.  However, I just use my handy local linux machine instead of logging into a remote server because some times the remote one is slow or down.  There is a difference though, in the display.  The remote server will display memory contents in Big-Endian, while my linux box displays them in Little Endian. This can get confusing.  Here is an example: 

Remote server (libra):  

libra% od -x file.txt
0000000 4120 7465 7874 2066 696c 650a 5468 6973


my local machine: 
neal@neal-desktop:~/workspace/SFSU/compsci/csc310/lab$ od -x file.txt
0000000 2041 6574 7478 6620 6c69 0a65 6854 7369


Both machines are displaying the same file, but the numbers are backwards. 



Is there a way to have my local machine display the code in Big-Endian?  Or is this an actual storage issue for the hardware in my machine? 

Thanks! 

Neal

---

### Post by Pro-reason on 2008-09-14
Would this help?

[http://www.omnigroup.com/mailman/archive/macosx-dev/2006-July/059072.html](http://www.omnigroup.com/mailman/archive/macosx-dev/2006-July/059072.html)

It's too technical for me.

---

### Post by deijsman on 2008-09-15
It's likely that the server is a Big-endian machine.  Is sounds like you want to convert the data.  The prev. link should do.

---

### Post by imneal on 2008-09-15
Thanks!  That helps a little, because I think that it points me to the architecture of the remote server (Sun Sparc CPU) is big endian, and (maybe) my amd 64 phenom is little endian.  I guess most (or all) x86 architecture is stored in little endian. 

I don't really understand how to use the code on the link you provided though... and I think it converts from Big-Endian to native (which I don't understand what native would be... why not convert from Big to Little endian or  vise versa? Those are your only options)



Does anyone know of a way to convert the Little Endian display to be Big Endian?

---

### Post by Pro-reason on 2008-09-15
I don't actually understand endianness, or the code in the link I gave you (:lolflag:), but I do know bash.

[php]
#!/bin/bash
## egg-turner.sh

# Run through the input, grabbing each line
while read INPUT_STUFF; do

 # Grab that 7-number thingy, and display it in bold
 SEVEN="$(echo $INPUT_STUFF | cut -b 1-7)"
 echo -ne "\033[1m"$SEVEN"\033[m"

 # Grab the rest of the line
 CHUNKS="$(echo $INPUT_STUFF | cut -b 9-)"

 # Run through, grabbing each 4-character chunk
 for CHUNK in $CHUNKS; do
   # Grab each pair of numbers
   beginning="$(echo $CHUNK | cut -b 1-2)"
   ending="$(echo $CHUNK | cut -b 3-4)"
   # Display the other way round
   echo -n " $ending$beginning"
 done

# Insert a line break
echo
done
exit
[/php]

As far as I can tell, that will turn things around the way you want.

Save it as &#8220;egg-turner.sh&#8221;, then do &#8220;chmod +x egg-turner.sh&#8221;, then do:

```

od -x file.txt | ./egg-turner.sh

```[PHP][/PHP]

If you put the script in /usr/local/bin, then it will be accessible from any directory, and you won't need to put &#8220;./&#8221; at the beginning of it.  Don't forget to install the script on the other machine if you want to run it there.

---

### Post by lisati on 2008-09-15
I'm sometimes baffled by the terms "big-endian" and "little-endian". Having said that, however, there is one thing which may be of interest: the suggestion that the computer architecture is probably an important factor. When an x86 processor loads a 2-byte word into a 2-byte register from memory, it is common for the bytes to be swapped. This means that the sequence 1234 stored in memory will often be loaded into the register as 3412. On the IBM mainframe I first learnt ASM on, it would've been more common for the register to end up with the more intuitive 1234.

As for the term "native", that is commonly used to describe what is "natural" to the particular processor and/or OS that one happens to be using at the time.

---

### Post by imneal on 2008-09-15
Wow, you guys rock.  Thanks Pro-Reason for the code.  That's a great way to make it display what I want to.  I'm really beginning to like Linux! 

I think the architecture has a lot to do with it, and I'll be keeping that in mind as I run through MIPS. 


Thanks again!

---

