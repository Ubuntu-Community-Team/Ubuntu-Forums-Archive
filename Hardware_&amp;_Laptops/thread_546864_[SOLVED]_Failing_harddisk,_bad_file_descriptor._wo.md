---
title: "[SOLVED] Failing harddisk, bad file descriptor. workaround in package manager?"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by martijn hoekstra on 2007-09-09
I cannot access the file '/usr/share/gimp/2.0/gradients/CD.ggr' due to an invalid file discriptor. This seeems to be a headdisk failure, but now I have no idea to correct it. What I would like most is to be able to delete said file, but I would settle for a workaround where I can trick my system into thinking it doesn't have the Gimp package installed, and it will leave the broken file in peace. It's a crippling situation, as every apt-get operation is failing, because it will try to uninstall the gimp first, and then fail and abort. So these are basicly two questions:

1. How can I make my system ignore the package the Gimp completely

2. How can I fix the disk problem

Help would be greatly appreciated.

---

### Post by El Rogueo on 2007-09-09
> **martijn hoekstra said:**
> 

1. How can I make my system ignore the package the Gimp completely

2. How can I fix the disk problem



I can imagine how crippling that is, because I end up killing everything through apt-get. If you fix the disc problem first, you'll probably have better odds on killing it.

What do you mean by having ubuntu ignore it? Make it invisible to the user? Remove it from the program menu?

As for the disk problem, exactly what kind of problem is it? Is it actually a "head" problem or is that a spelling mistake? Head crashes, where the read head smashes into the fast-spinning and highly sensitive surface of the hard drive platter, tend to be the kind of thing you can't fix, and also lead to severe data loss and eventual complete hard drive failure. Is there a more descriptive explanation of what's wrong with the disc?

Some cheap (and relatively invasive) fixes are low level formatting and bad sector repair. There are various programs to do both, although the simplest way to do so is to go to the website of your hard drive manufacturer and get a bootable CD image of a "diagnostic" or "maintenance" tool kit. If you burn that you should be able to fix some problems like that.

Bad sector repair etc is non-invasive and won't damage data. A low-level format, on the other hand, manually writes the whole drive to zeros. It's also known as a factory-wipe. If a low-level format won't fix it, you're going to end up spending money to fix it, either through mailing it back to the manufacturer for repair, or simply in having to buy a new one.

---

### Post by El Rogueo on 2007-09-09
A bad file descriptor indicates a corruption in the file system, according to Google, and can be repaired with the command "fsck" according to the FreeBSD community. This thread is relevant:

[http://ubuntuforums.org/showthread.php?t=10030](http://ubuntuforums.org/showthread.php?t=10030)

short of finding this mysterious fsck, you can also try this:

[http://ubuntuforums.org/showthread.php?t=295262](http://ubuntuforums.org/showthread.php?t=295262)

---

### Post by martijn hoekstra on 2007-09-09
Thank you for your reply!

I didn't get Bonager to work, but I might still. Fsck for some reson thinks my filesystem is clean, while it really isn't, as stuff is broken. I think it's a bad file descriptor, because that is what synaptic reported in its status window, but that might ofcourse be wrong, where synaptic assumes that is the problem, but it really isn't. the following is some of the strange output from a root terminal:

ls -la:
>  ls -la
total 0
drwxr-xr-x 2 root root 72 2007-08-31 16:02 .
drwxr-xr-x 3 root root 80 2007-09-06 12:44 ..
?--------- ? ?    ?     ?                ? CD.ggr


touch CD.ggr
> 
touch CD.ggr 
touch: cannot touch `CD.ggr': Permission denied


that cannot <something> `CD.ggr`:permission denied is what every operation I tried gives me.

What I meant with ignoring the package, is that my system will not try to update or remove the Gimp package, just pretend it's not installed, and that it doesn't need further removing/updating. Putting the package on hold with dpkg --set selections doesn't work, I get the following output from apt-get upgrade:

> 
The following packages will be REMOVED:
  gimp-data
The following held packages will be changed:
  gimp-data


and the updating process stops as it tries to update or in this case remove the package gimp-data.

---

### Post by martijn hoekstra on 2007-09-09
if there is anyone else who might be able to help me with this problem I would be delighted.

---

### Post by martijn hoekstra on 2007-09-10
I managed to create a workaround, by editing /lib/var/dpkg/info/gimp-data.list and removing the offending file. dpgk now figured it was able to remove the gimp-data package, and carry on functioning normally. This doesn't fix or mark the disk error, but at least we can now all stick our heads down the send, and continue functioning normaly, pretending it never happned.

---

