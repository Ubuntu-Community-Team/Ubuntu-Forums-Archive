---
title: "Installation of USB jostick"
date: 2005-03-07
forum: Hardware &amp; Laptops
---

### Post by dmoyne on 2005-03-07
I have a analog **joystick** plugged into a **USB port** ; most game applications expect js0 to be in "**/dev/js0**" to interface a joystick ; with Ubuntu js0 is located under "**/dev/input/js0**" so I can create a soft link from "**/dev/js0**" onto "**/dev/input/js0**" to make it work but can I get such set up permanent at each boot session ?
Thanks

---

### Post by watchitman on 2005-03-19
I'd like to know this as well.

---

### Post by honeywelljr on 2005-04-19
I was wondering if anyone ever got an answer to this?  I was just trying to find the answer to this question.

---

### Post by DanP on 2005-05-16
The first thing that comes to mind is to make a script in /etc/init.d/
which will create the link for you-- something to the effect of:
(You will need to be root for the following)
make a text file containing:

  #!/bin/sh

  ln -s /dev/input/js0 /dev/js0


name it "S99local"

so it will execute near last

make the script executable:

chmod a+x ./"S99local"


then make a link to it either in /etc/rcS.d or
/etc/rc2.d (or whatever your default run level is)
"/etc/rcS.d" is my prefered as these links get run only once at boot time,
so I don't have to worry about runlevel changes and such.
Obviously someone with real scripting ability could do much better.

you may not want to make the script excutable by
everyone, see the  man page for chmod for more info.

I don't know if this is the Ubuntu way, but it will get the job done.

Any other boot time commands can be added to the same file, for example:



#!/bin/sh

  ln -s /dev/input/js0 /dev/js0

  another command

  another command

always end the file with a return,or possibly an "exit" command (see man bash).

For more info
see the man pages for:
chmod
bash
chown
ln
and the scripts in /etc/init.d to see how these scripts should really
be written. 

I have used this same method to load drivers, delete links, start daemons, etc. at boot.

HTH,

DanP.

---

