---
title: "How do you install drivers for un detected pc cards"
date: 2006-02-06
forum: Hardware &amp; Laptops
---

### Post by Brigrat on 2006-02-06
I have a pc network card that goes undetected during install.  i have the drivers for it but am not sure how to install them.

---

### Post by narcoti on 2006-02-06
hey dude im in the sam boat here is my jist
:cry: Ok I have a 4 year old Sony Viao laptop that origanaly came with no ethernet got that much. But it did come with two pcmcia ports on whicth I origanally placed a netgear wireless adapter and a d-link ethernet adapter both of witch worked when I had windows. Now when I started to install unbuntu on my laptop everything went fine untill I got to the network part of it. Unbuntu did not recognize either of my adapters by this time I think I was to far to stop the instalation so I continued. I was now completely finished with installing Unbuntu. I now look at both of my instalation disks and for the d-link one I could not install regularly , but I did find a linux driver for my d-link on the disk but unlike on windows were it installs it for you there are no instructions or any executable  just 2 files that one ends in .c and the other ends in .h now when i opened them up they one time showed as just being on text editor  but the next time I open them I try a different way  and little black window pops up  and goes away real quikly and does nothing that I am aware of no conformation or anything............................ help..........

---

### Post by Nightwind on 2006-02-06
[QUOTE=Brigrat]I have a pc network card that goes undetected during install.  i have the drivers for it but am not sure how to install them.[/QUOTE]
Hey check this post out and see if it helps on the driver issue
Post back if this doesn't resolve the issue
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

### Post by narcoti on 2006-02-06
that really didnt help me as I need a dumbed down version on how to install the drivers that i have.....

---

### Post by Nightwind on 2006-02-06
[QUOTE=narcoti]that really didnt help me as I need a dumbed down version on how to install the drivers that i have.....[/QUOTE]
Narcoti what type of drivers are you trying to install if I might ask? I will try to help you but I am not a linux/computer guru by any means.
You might also try this link [http://pcmcia-cs.sourceforge.net/](http://pcmcia-cs.sourceforge.net/)

---

### Post by mohapi on 2006-02-07
[QUOTE=narcoti]hey dude im in the sam boat here is my jist
:cry: Ok I have a 4 year old Sony Viao laptop that origanaly came with no ethernet got that much. ...[/QUOTE]
I was just wondering if your problem was similar to [mine]("http://ubuntuforums.org/showthread.php?t=125334"), or if it differs somehow.  I have a feeling my laptops predate yours by a few years more. Just curious, though. Thanks.

---

### Post by Nightwind on 2006-02-07
[QUOTE=mohapi]I was just wondering if your problem was similar to [mine]("http://ubuntuforums.org/showthread.php?t=125334"), or if it differs somehow.  I have a feeling my laptops predate yours by a few years more. Just curious, though. Thanks.[/QUOTE]
Follow the instructions on this site.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)
Pretty detailed instructions, hope it helps

---

### Post by Nightwind on 2006-02-07
[QUOTE=Brigrat]I have a pc network card that goes undetected during install.  i have the drivers for it but am not sure how to install them.[/QUOTE]
Instructions here [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

---

### Post by narcoti on 2006-02-09
[QUOTE=Nightwind]Narcoti what type of drivers are you trying to install if I might ask? I will try to help you but I am not a linux/computer guru by any means.
You might also try this link [http://pcmcia-cs.sourceforge.net/](http://pcmcia-cs.sourceforge.net/)[/QUOTE]
 these are the drivers [http://support.dlink.com/faq/view.asp?prod_id=1226&question=DFE-690TXD](http://support.dlink.com/faq/view.asp?prod_id=1226&question=DFE-690TXD)

---

### Post by narcoti on 2006-02-09
[QUOTE=mohapi]I was just wondering if your problem was similar to [mine]("http://ubuntuforums.org/showthread.php?t=125334"), or if it differs somehow.  I have a feeling my laptops predate yours by a few years more. Just curious, though. Thanks.[/QUOTE]
i have model  PCG-748

---

### Post by narcoti on 2006-02-11
Please I just need to know what to do with the drivers that I already have as I cannot find any manual what so ever.

---

### Post by narcoti on 2006-02-11
I have the drivers as you can see but I am so so new to liux I have no earthly idea on how to install them btw I used the device manager and there are no options to chang any settings what so ever but I will point out that it did recognize my pmcia cards but i dont know what to do as I know no commands for unbuntu  i would like to have like a manual that would show me how to use termanle. Oh the connection that is set up on it right now lis like a loopback think and it has a place to change the connection type but the drop down list only has one option, the loopback thing :(

---

### Post by K.Mandla on 2006-02-11
[QUOTE=narcoti]i would like to have like a manual that would show me how to use termanle.[/QUOTE]
This might help you with setting up the drivers. ...

[https://wiki.ubuntu.com/WifiDocs]("https://wiki.ubuntu.com/WifiDocs")
[https://wiki.ubuntu.com/HowToSetUpNdiswrapper]("https://wiki.ubuntu.com/HowToSetUpNdiswrapper")
[https://wiki.ubuntu.com/NetworkCards]("https://wiki.ubuntu.com/NetworkCards")

If you need more help or want more information, try out the whole wiki. ...

[https://wiki.ubuntu.com/UserDocumentation]("https://wiki.ubuntu.com/UserDocumentation")

And don't forget the help button on the desktop. It looks like a life preserver. ;)

---

### Post by Nightwind on 2006-02-14
[QUOTE=narcoti]I have the drivers as you can see but I am so so new to liux I have no earthly idea on how to install them btw I used the device manager and there are no options to chang any settings what so ever but I will point out that it did recognize my pmcia cards but i dont know what to do as I know no commands for unbuntu  i would like to have like a manual that would show me how to use termanle. Oh the connection that is set up on it right now lis like a loopback think and it has a place to change the connection type but the drop down list only has one option, the loopback thing :([/QUOTE]
If you will read the instructions on the link you will learn how to install the drivers. It will require reading and doing it. It's not hard  just takes time.

---

### Post by K.Mandla on 2006-02-14
[QUOTE=narcoti]I have the drivers. ... I will point out that it did recognize my pmcia cards. ...[/QUOTE]
If it has recognized your card, then you're headed in the right direction. 

Try this: Start the terminal with Applications > Accessories > Terminal. Then. ...

```
sudo apt-get install ndiswrapper-utils
```
That should ask you for the Ubuntu installation CD, then install ndiswrapper. If not, you can copy it from the CD. It's inside /pool/main/n/ndiswrapper, and it's called ndiswrapper-utils_1.1-4ubuntu2_i386.deb. If you have to copy it over, you can install it with *sudo dpkg -i ndiswrapper-utils_1.1-4ubuntu2_i386.deb*; I see it needs libc6 and perl, but I believe those are in place with every Breezy install. (Can someone correct me on this?)

Once you get ndiswrapper installed, you need to find the .inf file for your wireless card. Copy it into your home directory with the File Browser. If there is a .sys file that matches it, copy that too (I have heard that some installations need the .sys file too).

Then do this. ...

```
sudo ndiswrapper -i _________.inf
```
Type the name of your .inf file in the blank above. Then hit enter, and it should install your driver. You can find out with this:

```
ndiswrapper -l
```
If you see "hardware present, driver present", then you're set! But anything else is a problem.

Then. ...

```
sudo modprobe ndiswrapper
```
and

```
sudo ndiswrapper -m
```
If you're lucky, it will be working now. You might have to use the Networking tool in System > Administration > Networking to configure your network.

Good luck. It's not as difficult as it sounds! :D Remember, if you need better instructions, [read the wiki]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=HowToSetUpNdiswrapper").

---

