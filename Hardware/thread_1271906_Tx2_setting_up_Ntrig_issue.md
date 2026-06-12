---
title: "Tx2 setting up Ntrig issue"
date: 2009-09-21
forum: Hardware
---

### Post by IamGibby on 2009-09-21
So I've been following the guide [@ubuntuforums.org]("http://ubuntuforums.org/showthread.php?t=1252492&highlight=tx2+jaunty") and I've ran into an issue. I'm on step 3 of the guide where we have to enter:

```
gksudo edit /etc/X11/xorg.conf
```into the terminal, and I'm getting an error back that I can't seem to figure out (I've had 1 or 2 errors along the way that I've figured out so far but I'm extremely new to linux and am learning as we speak)

Error:

```
~$ gksudo edit /etc/X11/xorg.conf
Error: no "edit" mailcap rules found for type "application/octet-stream"
/octet-stream"

```Thanks for any help anyone has to offer.

---

### Post by Ayuthia on 2009-09-21
> **IamGibby said:**
> So I've been following the guide [@ubuntuforums.org]("http://ubuntuforums.org/showthread.php?t=1252492&highlight=tx2+jaunty") and I've ran into an issue. I'm on step 3 of the guide where we have to enter:

```
gksudo edit /etc/X11/xorg.conf
```into the terminal, and I'm getting an error back that I can't seem to figure out (I've had 1 or 2 errors along the way that I've figured out so far but I'm extremely new to linux and am learning as we speak)

Error:

```
~$ gksudo edit /etc/X11/xorg.conf
Error: no "edit" mailcap rules found for type "application/octet-stream"
/octet-stream"

```Thanks for any help anyone has to offer.

Welcome to the forum!

It looks like you are only missing one character.  The editor in Ubuntu is called gedit so to edit the file:
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by IamGibby on 2009-09-21
Yea I noticed the g wasn't typed there, but it was the way the tutorial had it.. so refraining from just trying it myself and messing it up, I posted here.. thanks.

> **Favux said:**
> To edit it enter in a terminal:
```
gksudo edit /etc/X11/xorg.conf
```

---

### Post by IamGibby on 2009-09-21
To keep this all in 1 section for me to remember, I have a few other questions.

First, is it possible to change the bootloader's names for partitions when loaded? Like it lists all the ubuntu's and will auto run ubuntu after 10 seconds, but I have 2 Vista partitions, 1 is the OS the other is the recovery, I would really like to label (Recovery) at the end of the second Vista drive so It looks better ( I know the top one takes you to the OS but still)

is it possible with out messing up the bootloader? (Yes, I've searched but no luck =S)

---

### Post by Ayuthia on 2009-09-21
> **IamGibby said:**
> To keep this all in 1 section for me to remember, I have a few other questions.

First, is it possible to change the bootloader's names for partitions when loaded? Like it lists all the ubuntu's and will auto run ubuntu after 10 seconds, but I have 2 Vista partitions, 1 is the OS the other is the recovery, I would really like to label (Recovery) at the end of the second Vista drive so It looks better ( I know the top one takes you to the OS but still)

is it possible with out messing up the bootloader? (Yes, I've searched but no luck =S)

Yes it is.  You can edit the menu.lst file for GRUB:
```
gksudo gedit /boot/grub/menu.lst
```
If I recall correctly, the Vista information is at the bottom of the file.  It should look something like:
```
title       Windows 7 RC (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader +1

```
You can go into the title line and change to the name to whatever you like.

---

### Post by IamGibby on 2009-09-21
Another noob question (this thread can be deleted by an admin once I ask all my questions if they want, since its been derailed so many times)

I'm new to the Package installation setup, I can't figure out how to get flash enabled in my Mozilla firefox.. I've tried 2 or 3 of the quick search results 'flash' which are like flashmozillaplugin and Flashfreesomething and non of them make flash work in the browser, tried to go to the adobe website and tried a manual install but it gives me like 6 different Linux options of which non I know how to execute.

Secondly, I wanted to put in my ATI graphics drivers to see if I could try to use Compiz-Fusion (when I enable it atm, it says unable to)

Dunno if it makes a difference if my gfx card on this Tx2 is only 64mb or not.

Any suggestions? Thanks.

---

### Post by Ayuthia on 2009-09-21
> **IamGibby said:**
> Another noob question (this thread can be deleted by an admin once I ask all my questions if they want, since its been derailed so many times)

I'm new to the Package installation setup, I can't figure out how to get flash enabled in my Mozilla firefox.. I've tried 2 or 3 of the quick search results 'flash' which are like flashmozillaplugin and Flashfreesomething and non of them make flash work in the browser, tried to go to the adobe website and tried a manual install but it gives me like 6 different Linux options of which non I know how to execute.

Secondly, I wanted to put in my ATI graphics drivers to see if I could try to use Compiz-Fusion (when I enable it atm, it says unable to)

Dunno if it makes a difference if my gfx card on this Tx2 is only 64mb or not.

Any suggestions? Thanks.

Can you let us know if you are using 32 or 64 bit?  The 32-bit version is:
```
sudo apt-get install flashplugin-nonfree
```

If you are using 64-bit, you can try the following link:
[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

I have not tried it that way, but it should work.  Worst case, we can try to it one step at a time.  The 64-bit is a little more tricky right now because Adobe has not released the final version of it yet.

---

### Post by IamGibby on 2009-09-21
Yea I am using 64BIT AMD.. Flash can wait, what's really twisting my nervs is updating this factory Mozilla FireFox Browser... I can not seem to figure out a way to get to 3.5 instead of 3.0 (my bookmarks and stuff didn't xfer over from my Vista when it asked if I wanted it to, so i think it might be because of the different Firefox version?)

But yea I've tried to search both "Mozilla' and "Firefox" in the Package Manager and tried a few different installs that looked like they would update the browser but no go... any thoughts of what my linux-eliterate self can't figure that type of stuff out yet.

---

### Post by Ayuthia on 2009-09-21
> **IamGibby said:**
> Yea I am using 64BIT AMD.. Flash can wait, what's really twisting my nervs is updating this factory Mozilla FireFox Browser... I can not seem to figure out a way to get to 3.5 instead of 3.0 (my bookmarks and stuff didn't xfer over from my Vista when it asked if I wanted it to, so i think it might be because of the different Firefox version?)

But yea I've tried to search both "Mozilla' and "Firefox" in the Package Manager and tried a few different installs that looked like they would update the browser but no go... any thoughts of what my linux-eliterate self can't figure that type of stuff out yet.

Karmic Koala is coming out towards the end of October and it will have 3.5 instead of 3.0.  You might wait for that.  Jaunty does not go to 3.5 only because it is a version upgrade instead of a security update.  Since a new version of Ubuntu comes out every six months, they will provide updates to packages but they don't do version updates.

There are ways to install Firefox 3.5 into Jaunty, but it is not part of Ubuntu.  For example, there is this link:
[http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/](http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/)

I never tried it, but it is a script that will install 3.5 in Ubuntu.  I am not for sure if it will work for you or not, but it is a method that you can try.  You might even post another thread and ask if there is an easy way to do it.

You might just try Jaunty out for a while so that you can get used to Linux.  Like I said, Karmic is coming out next month and it will be a little easier to use for the TX2.  I say this because the kernel that Karmic uses will have a more up to date version that will support the touchscreen better.  There will still need some work to make it all happen, but it should not be as bad.

---

### Post by IamGibby on 2009-09-22
Thanks for the heads up.. I'll start searching for how to update ubuntu dunno if i'll need to rip another live cd or if you can do it within the OS if you have it pre-existing partitioned.

Thanks for everything,

Chris.

---

