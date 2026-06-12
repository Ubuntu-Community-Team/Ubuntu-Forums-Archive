---
title: "Intel i855 graphics on Ubuntu 10.10 frustration"
date: 2010-11-26
forum: Hardware
---

### Post by markoid63 on 2010-11-26
Please please help. I have the notorious Intel i855 graphics chip and am using Ubuntu 10.10. I have tried all the tricks I could find, managed to enable the proper Intel drivers, but suffered all the usual glitches (no mouse pointer, no background, freezes etc.). I tried installing the patch that is supposed to help, but could not get it to install. Running without those drivers works okay but video is choppy, and little freezes of the mouse are frustrating. I also want to play some basic games but can't. I love using this system, better than Windows, but I might have no alternative but to go back to it if I can't get this sorted. Does anyone know how to help, I'm begging! :confused:

---

### Post by Anthony25 on 2010-11-28
Hi,
I am running on ubuntu 10.10 on my laptop with the chipset intel 855GM too. I have found a "solution" (because it doesn't fix all bugs) that is to install a different kernel that the official'.

Download files on this address : [http://people.canonical.com/~ogasawara/lp614176/i386/]("http://people.canonical.com/%7Eogasawara/lp614176/i386/")
and put them in the same folder (for example in the folder "Linux" in your home).

Then you open the terminal, and you type :

**cd /home/(the_user_name)/Linux       **(You go in the folder where you have put your files, here it's an example that I have took)
[B]sudo dpkg -i *.deb

[/B]It's installing the kernel.

Then you have to modify the configuration of Xorg :
In the terminal you type :

[B]sudo gedit /etc/X11/xorg.conf

[/B]And you paste this :


[I]Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"[/I] [I]
        Identifier      "Configured Monitor"
EndSection

Section "Screen"[/I] [I]
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection [/I]


Save and reboot.
In grub boot on the kernel 2.6.35-22.32+lp614176

If you want to delete the official kernel you have to uninstall the package "linux".

**Don't update your kernel, because it will reinstall the official kernel.**


PS : sorry for my bad english, I am french ;)

---

### Post by markoid63 on 2010-12-02
Thankyou for your response, glad you got it working. But this shouldn't be that hard, and I found a solution - I installed Fedora 14, and it works perfectly with all effects. Why couldn't Ubuntu do this?  :p

---

### Post by ImConfused on 2010-12-13
Is Ubuntu going to be able to come up with a solution for the i855 problem before 9.10 becomes outdated?  I updated to 9.10 from 9.04 because 9.04 reached the end of its term of support.  I tried the Fedora 14 live disk and it seemed that they did not have a problem with the i855 graphics chip unlike Ubuntu 10.04 and 10.10.  I am booting off of a non bootable USB stick so as to not touch my laptop's Windows XP hard drive for Linux.  I managed do it in Ubuntu.  The problem is whether I will be able to do this with Fedora should Ubuntu not have this solved when 9.10 becomes outdated.  I have become used to Ubuntu even though I do experience the occasional freeze that now I know may be due to the i855.  

Thanks for the Fedora information.  I hope when the time comes I don't need to change to Fedora but now I know that there is an option that I can persue should it become necessary when 9.10 is no longer supported.

---

### Post by Mckormick on 2011-01-19
Hi - I have exactly the same problems as the OP, is there a fix for this other then switching distros?

---

### Post by Anthony25 on 2011-01-31
Hi,
Read my post, I have found a possibly fix (that doesn't fix all problems we have with this chipset), and ask me if you have some problems with.

I say it again : sorry for my bad english, I am french ;)

---

