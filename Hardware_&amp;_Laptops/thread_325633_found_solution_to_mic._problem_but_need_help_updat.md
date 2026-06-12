---
title: "found solution to mic. problem but need help updating my drivers"
date: 2006-12-26
forum: Hardware &amp; Laptops
---

### Post by kolinab on 2006-12-26
Hi,

I've got a Dell 630m with ICH6 sound. I've found what I think is the solution to the well documented problem getting the microphone input working, but I don't know how to edit the files people are talking about or how to compile or anything.

I wonder if someone can hold my hand through this a little bit. Here's the bug I wanna fix:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/42600]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/42600")

and I'm pretty sure I found the solution is to update my ALSA drivers, but apparently this involves compiling from sourc, and I don't know how. [Here's the page at ALSA]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+AC97+audio.&chip=440MX%2C+i810%2C+i810E%2C+i820%2C+ICH4%2C+ICH5%2C+ICH6&module=intel8x0").

Like I say, I've googled the heck out of this problem and I think I have the solution, but I just don't know enough to do this. I'd love it if someone could give me a tip or two to get me in the right direction.

Thanks,

Kolin

---

### Post by foolsh on 2006-12-26
compiling any source code is pretty easy once you find out how
first of all you will need a compiler and build tools
this can be installed very easily in ubuntu with
```
sudo apt-get install build-essential
```

since this is kernel module package you will need the souce for the kernel headers too i believe
```
sudo apt-get install linux-headers-`uname -r`
```

next download the source you want compiled and decompress it to a folder in your home directory 
this step is different for every source code package 

in a console navigate into the source directory to where the file named configure.sh is. its usually in the first directory of the source. some times its in an directory named tools
and some source packages have install.sh instead.

some helpful console commands are ls and cd.
 ls - list(s) the directory contents you are in, and cd - changes directory like `#cd alsa`

when you are in the directory with configure.sh or install.sh run command
```
./configure
```
or
./install.sh
in this step watch the output for error messages ones the end with can not find libsumfilename and such you can try installing said file by using a command like sudo apt-get install libsumfil* and hope for the best

after confiure.sh is finished with no error messages run the command
```
make
```

if make finishes without errors

```
sudo make install
```

if you get errors google is your friend :)

---

### Post by kolinab on 2006-12-26
Thanks a lot for the detailed reply. I'm going to sit down and attack this problem today. I'll post my results certainly. I guess this is only a Kernel module I need to deal with.

---

### Post by kolinab on 2006-12-26
OK - I'm excitedly close to solving my problem. Looks like I might not need to recompile anything. What I need to is:

append the following to the end of my tc/modprobe.d/alsa-base file:

options snd-hda-intel model=ref

So I open the file in Gedit but it's read only. So I must have to sudo  . . . somehow so I have permission to do this. How do I do it?

---

### Post by kolinab on 2006-12-26
OK, so this is a dialogue with myself. But I'm getting there. I decided to post my answer to myself because searching forums lately for troubleshoothing, it seems lots of people don't post their answers once they get stuff working. It's excruciatingly simple what I did.

[code]

gksudo gedit /ect/modprobe.d/alsa-base

And saved my changes to the document. Now I'm going to reboot and try my microphone. Fingers crossed.

---

### Post by kolinab on 2006-12-26
I rebooted and my microphone is working. I am so pleased! Now I must post my solution to other message boards . . . !

---

### Post by alex.vice.grab on 2007-03-21
It worked!!! Thank you, that's what happens when you have a community of open source users, they help each other :)))
Thanks again,
Alejandro

---

