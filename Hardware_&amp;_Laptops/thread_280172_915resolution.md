---
title: "915resolution"
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by hz1840821 on 2006-10-19
Hi everybody,

I'm sorry to recall one the most boring and redundent topics :) but I have to](*,) 
I have an Intel videocard and I would like to see things with the right resolution, 1280x800 for instance.
When I execute the command line
sudo 915resolution 38 1280 800
and then I restart the Xserver by pressing ctrl+alt+backspace, then I get the desired resolution. 
That I do not know is how to execute 915resolution directly when booting, before the X server get started.
I tryed with rcconf package, but it didn't help. 915resolution appears in /etc/init.d but something is still not working.

Can anybody help me with this matter? Or maybe just show me a good howto :-k ...
Thanks

---

### Post by Kateikyoushi on 2006-10-19
Actually this should be enough

```
sudo aptitude install 915resolution
```

In case it is not create an initscript for it. [LINK]("http://linuxmint.com/content/view/212/52/")

---

### Post by hz1840821 on 2006-10-19
Still not working ](*,) 
915 was installed and put in the program list to start when booting. But I'm doing smth is wrong :-k 

FRANCO

---

### Post by jayson23 on 2006-10-29
I'm in the exact same boat. I have to manually run 915resolution every time I restart. 

It's a pain in the behind, and certainly makes Ubuntu look unattractive whenever a friend sees me start my computer. I've had a few people watch me go into the terminal and restart X just to get my screen looking right, then say "I thought Ubuntu was supposed to be easy to use?" to which I have to tell them, "Yeah, but I just can't figure out how to make the screen resolution work right."

Could someone PLEASE give easy newb steps for this? Every answer I've read seems to be missing the essential element of simply getting the darn computer to look right when it starts up, not when you go through manually configuring 915resolution.

I'm using 6.10 on a Fujitsu P5010, by the way.

Thanks!

---

### Post by antibiotek on 2006-10-29
Here guys, this should do it:

[http://www.ubuntuforums.org/showpost.php?p=842543&postcount=8](http://www.ubuntuforums.org/showpost.php?p=842543&postcount=8)

---

### Post by Eleka on 2006-10-30
I have the same issue when I sart my laptop, but, if I do "sudo 915resolution 38 1280 800" and restarted Xorg I'm having the same issue.

When I put "sudo 915resolution -l" before that I don't have a 1280x800 mode. When I follow the step of 915resolution 38 1280 800 and re-do the 915resolution -l, I can see that mode and I think that it's ok.

I restarted my xorg and then all is like before: 1024x768 resolution and, in the resolution selector, only 3 modes: 1024x768, 800x600 and 640x480.

In my xorg.conf I only have configurated one mode, 1280x800, but it don't works for me ...

Some idea?

---

### Post by jayson23 on 2006-10-30
I'm far too newb to know who this will or won't work for, but I finally got my Fujitsu P5020 to start up with the correct resolution, thanks to this page: [http://linuxmint.com/content/view/212/52/](http://linuxmint.com/content/view/212/52/)

I installed 915resolution, and was able to get it working with the resolution I wanted ( 1280 x 768 ), but up until now, I had to manually run it every time I restarted.

After going through the above link, I found out I had done two things wrong.
First, the "widescreen" script I created didn't have the correct permissions. I just changed it to 777 - hopefully this won't cause any problems?

I also had the link in /etc/rc2.d named so that it was starting too late. Renaming the link made 915resolution start earlier, and now my laptop is working with the correct resolution every time I start it up!



Here's the steps I followed - hope they can work for you as well:

1. install 915resolution

2. Create the file "widescreen" in /etc/init.d and make it executable:

[FONT="Courier New"][B]touch /etc/init.d/widescreen
chmod a+rx /etc/init.d/widescreen[/B][/FONT]

3. Edit the file and write the following into it ( I used gedit, to make it easier - [FONT="Courier New"]**sudo gedit /etc/init.d/widescreen**[/FONT] ):

**/usr/sbin/915resolution 5c 1280 768 32**

Of course, make sure /usr/sbin is the right path to your installed 915resolution, and that 5c and 1280x768 at 32bit are the options you want to give to it.

4. Go to the directory for Ubuntu's default run level, in this case **/etc/rc2.d** 

5. Create a link to run the widescreen script at startup:
[FONT="Courier New"][B]
ln -s /etc/init.d/widescreen /etc/rc2.d/S06widescreen
chmod 777 /etc/init.d/widescreen
chmod 777 /etc/rc2.d/S06widescreen[/B][/FONT]



This worked for me - if anyone sees a problem with the permissions that I set, please point out the error. Hope this helps.

---

### Post by chunk on 2007-01-03
> **jayson23 said:**
> I'm in the exact same boat. I have to manually run 915resolution every time I restart. 

It's a pain in the behind, and certainly makes Ubuntu look unattractive whenever a friend sees me start my computer. I've had a few people watch me go into the terminal and restart X just to get my screen looking right, then say "I thought Ubuntu was supposed to be easy to use?" to which I have to tell them, "Yeah, but I just can't figure out how to make the screen resolution work right."

Could someone PLEASE give easy newb steps for this? Every answer I've read seems to be missing the essential element of simply getting the darn computer to look right when it starts up, not when you go through manually configuring 915resolution.

I'm using 6.10 on a Fujitsu P5010, by the way.

Thanks!

All I had to do was install 915resolution using synaptic. After the first reboot it automatically worked and it's automatically worked ever since.

I'm running 6.10 (fresh install) on a Fujitsu P5010. On previous versions of ubuntu I had to make an init script to run it manually on every boot, write the 915resolution config file, etc, but with edgy I didn't have to do anything. Didn't even have to write the config file (the default "auto" config file just worked).

Did you upgrade to edgy or is it a fresh install? If you upgarded then I recommend you try a fresh install. Edgy seems to have a new init system in place.

---

### Post by cheaplow on 2007-01-04
I'm about to install 6.10 on my P5010 this weekend.  Would like to hear your experience.  Things went smoothly for you?  Any hardware compatibility issue?  Thanks!!!!

---

### Post by oscariommi on 2007-09-11
I now where the problem lies:

I installed 915resolution. And I had exactly the same problem: Having to manually run 915resolution, even though it has installed itself in /etc/init.d/.

I found that it for some reason exits on the chipset-test. Well I installed it because I DO have one of the intel chipsets.

**DIRTY SOLUTION:**
sudo vim /etc/init.d/915resolution
(use *your* favourite editor ofcourse!)

Comment out the line:
$PROG -l >/dev/null 2>&1 || wrong_chipset

like so

#$PROG -l >/dev/null 2>&1 || wrong_chipset - DIRTY FIX!


Now, it starts, but still I have to three-finger-salute X11 once to get the right resolution.

In /etc/rc.d/ I find: **S20915resolution**, *but * I also notice: **S13gdm**. GDM is started before 915res! 915res is a BIOS-patch-thingie. Think BIOS. Think first. Think _early_.

**SOLUTION:**
sudo mv S20915resolution S07915resolution

Number 07 is arbitrary. The really important thing is put it *before gdm!*

Hope this helps someone! I don't know who made the install-scripts and stuff for 915res, but ofcourse it should be changed to be focused on early ;-)

Thanks to everyone for all abundant help, helping me find 915res!

Oscar Campbell

---

