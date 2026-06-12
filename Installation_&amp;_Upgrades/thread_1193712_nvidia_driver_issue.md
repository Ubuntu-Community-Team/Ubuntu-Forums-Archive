---
title: "nvidia driver issue"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by Heldrex on 2009-06-21
I am having an issue with my nvidia drivers. I have dual nvidia geforce 8800's with sli and I need the driver for them. 

What I have done:

-I have done all of the updates when I first logged in. This installed the nvidia driver version 180. Upon restart I get hung up at "checking battery state [OK]"
-I also tried driver version 173, this had the same error as the other driver.

I have figured out how to access terminal, install packages and some other basic stuff but it's only been 24 hours using it. Just a heads up.

Edit: After trying the driver version 180 again I left the computer for a bit and just came back. The screen is now hung up on "reloading system log daemon..." I reinstalled the system and I have a fresh version on their now.

---

### Post by Heldrex on 2009-06-22
Update. I have also tried using Envy and came up with the same error... "Checking battery state.." This is a desktop so I don't have a battery. Is this a bug?

---

### Post by xtjacob on 2009-06-22
Have you tried going to the Nvidia site and downloading a driver?

---

### Post by ~sHyLoCk~ on 2009-06-22
Get the 185driver from nvidia's site and compile it yourself. There's detailed instructions too!

---

### Post by slamhound on 2009-06-22
I had the same problem when I installed two cards for use with three monitors (so no sli).  I fixed it by running nvidia-xconfig -a (as described in more detail in this reply to a previous poster: [http://ubuntuforums.org/showpost.php?p=7456283&postcount=12](http://ubuntuforums.org/showpost.php?p=7456283&postcount=12)_ )_. The "-a" tells nvidia-xconfig to configure all available gpus. I realize sli will probably lead to other issues, so this might not solve your problem.  But given that I got hung up in the same place ("checking battery state"), using nvidia-xconfig -a might also be a necessary first step for you.

Good luck.

---

### Post by Heldrex on 2009-06-22
> **~sHyLoCk~ said:**
> Get the 185driver from nvidia's site and compile it yourself. There's detailed instructions too!

I was at the website but got held up at a certain point so I tried doing it through applications. I tried running the script "sh NVIDIA-Linux-x86-185.18.14-pkg1.run" and that got this "sh: Can't open NVIDIA-Linux-x86-185.18.14-pkg1.run" I have the file sitting on my desktop and the file name is exactly that following the sh command. Am I doing something wrong or missing something?

---

### Post by xtjacob on 2009-06-22
When I installed my Nvidia driver i had to kill GNOME install it, and then start GNOME again.

---

### Post by Heldrex on 2009-06-22
I found a help for this on the nvidia forum and lost the link. (on a different computer now.)

I used this series of commands.

Log Out
Ctrl-alt-F1

sudo /etc/init.d/gdm stop

cd Desktop

Sudo  ./NVIDIA-Linux-x86-185.18.14-pkg1.run
This installed and when it went to compile it said it didn't find a program from NVIDIA and compiled itself. Is this right?

Sudo /etc/init.d/gdm start


Upon restart I got the battery hangup again. Do I have to configure something? Is there a way I can do that without reinstalling/repeating my process?

---

### Post by Arthur_D on 2009-06-22
> **Heldrex said:**
> I was at the website but got held up at a certain point so I tried doing it through applications. I tried running the script "sh NVIDIA-Linux-x86-185.18.14-pkg1.run" and that got this "sh: Can't open NVIDIA-Linux-x86-185.18.14-pkg1.run" I have the file sitting on my desktop and the file name is exactly that following the sh command. Am I doing something wrong or missing something?
Here's how I installed the NVIDIA drivers:
1. Hold CTRL+F1 to get to the terminal.
2. Write your login name and password.
3. Write "sudo /etc/init.d/gdm stop"
4. Use the cd command to get to the folder where the NVIDIA-Linux-x86-185.18.14-pkg1.run file is.
5. Write "sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run" and follow the instructions.
6. Write "sudo reboot", or use "sudo /etc/init.d/gdm start"(rebooting may be safest).
EDIT: Ah, you just beat me to it. Sorry, I have no clue what's going on.:)

---

### Post by Heldrex on 2009-06-22
No problem.

I think the issue is that I don't have the pre compiled kernel. While in the text only mode I am unable to access the internet through my router so it makes this difficult.

"No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel from {location}"
Answer: yes

Unable to connect

The installer will need to compile the kernel.

::compiles::

Would you like to run NVIDIA-xconfig utility to automatically update your x configuration file so that the NVIDIA X driver will be used when you restart X? Any pre-existing X config will be backed up.
Answer: Yes

sudo reboot

After that I get the hang up. Alt-F4 brings me back into the terminal. Once in the terminal I tried to run nvidia-xconfig -a but this had an error saying it
"could not open the device file /dev/nvidiactl"
"ERROR: Unable to determine number of GPU's in system; cannot honor '--enable-all-gpus' option"
"ERROR: unable to write to directory '/etc/X11/'

---

### Post by xtjacob on 2009-06-22
Yah I installed mine the same way except on a laptop. I was looking at [this]("https://bugs.launchpad.net/ubuntu/+bug/277587") link and someone said it wasn't really hanging they just had to hit a key and it kept booting. Have you tried that? Also what version of ubuntu are you running and what kernel are you booting up in?

---

### Post by xtjacob on 2009-06-22
This link might help also: [http://ubuntuforums.org/archive/index.php/t-1130157.html](http://ubuntuforums.org/archive/index.php/t-1130157.html)

---

### Post by Heldrex on 2009-06-22
I'm using Ubuntu 9.04 completely fresh install with all of the updates completed. My kernel is 2.6.28-13-generic

Gonna try hitting enter on that screen. I don't think it worked last time though.

Edit: It just skips down lines and I can type stuff. Doesn't do anything though.

---

### Post by Heldrex on 2009-06-22
When booting off of the 2.6.28-11 (I think that is the name) kernel I able to get in on a low graphics mode. In case that helps any.

---

### Post by xtjacob on 2009-06-22
Try booting into 2.6.28-11 and recompiling the driver for that kernel, and then rebooting in 2.6.28-11 again.

---

### Post by Heldrex on 2009-06-22
Got the same problem with that kernel. I rebooted off the first kernel in recovery mode and it still says I need to config x file when I go to driver settings.

EDIT: I am going to try using this guide. [http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185](http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185)

---

### Post by Heldrex on 2009-06-22
I reinstalled Ubuntu as 64 bit, because I thought that might be part of the problem. I then followed the guide through for 64 bit.

The command ```
sudo nvidia-xconfig
``` didn't work and I renentered terminal upon reboot.

I ran ```
sudo nvidia-config-a
``` then started gdm again, then rebooted. BAM everything is working, no more checking battery state.

It was an issue of the wrong bit and the wrong method of installation since it is a little buggy. At least I am a lot more familiar with linux now.

---

### Post by ratcheer on 2009-06-22
Sorry, edited due to confusion.

Tim

---

### Post by Heldrex on 2009-06-22
I think I might have an issue with my xserver. It's acting a little funny now. I felt the question belonged in another thread so I posted [here]("http://ubuntuforums.org/showthread.php?t=1194605") if anyone is following.

---

