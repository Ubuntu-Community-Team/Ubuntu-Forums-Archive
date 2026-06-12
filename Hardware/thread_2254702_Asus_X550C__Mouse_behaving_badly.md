---
title: "Asus X550C : Mouse behaving badly"
date: 2014-11-29
forum: Hardware
---

### Post by logie on 2014-11-29
I put 14.04 on my laptop and several things stopped working. I get by.  However, the mouse is really annoying me: every three seconds the pointer jumps 5mm to the left, and goes on doing this until it fetches up against the side of the screen.  I have never heard of such a thing! Has anyone any ideas please?

---

### Post by mörgæs on 2014-11-30
Which laptop?

---

### Post by logie on 2014-12-01
Asus X550C

---

### Post by mörgæs on 2014-12-01
With hardware that new I would use the latest of software, that is 14.10. 
How does it work in a live boot?

---

### Post by Pilot6 on 2014-12-01
Try to do

sudo gedit /etc/default/grub

Edit line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

si it looks this way

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux=1 i8042.noloop=1"

Save the file and run

sudo update-grub

Then reboot.

How  is the mouse?

---

### Post by logie on 2014-12-04
Thanks.  I put in sudo gedit /etc/default/grub and got in return

Warning: unknown mime-type for "etc/default/grub" -- using "application/octet-stream"
Error: no "edit" mailcap rules form for type "application/octet-stream"

(which means nothing to me).  Anything further please?

---

### Post by Pilot6 on 2014-12-04
Do you have Ubuntu or a flavor? Or you missed first "/".
You may try [COLOR=#000000] 
sudo nano /etc/default/grub

Ctrl+O to save, Ctrl+X to exit.[/COLOR]

---

### Post by logie on 2014-12-04
Thanks.
I tried to up-grade on-line and got a further problem:  an error message saying

E: dpkg was interrupted.  You must manually run 'dpkg-configure-a' to correct the problem.
E: _cache -> open () failed, please report.

How do I respond to this?
(I shall also try to boot to 14.10 from a disk.)

---

### Post by Pilot6 on 2014-12-04
It says what to do

sudo [COLOR=#000000]dpkg-configure -a[/COLOR]

---

### Post by logie on 2014-12-05
I have managed to do what you suggest.  It seemed to work in the terminal, but the mouse still does its jumping.  Thanks again: I am learning - a little.

Thanks.  I did it, and the problem has gone.

---

### Post by mörgæs on 2014-12-05
Good, please mark the thread 'solved'.

---

### Post by logie on 2014-12-05
Sorry: I am not sure that it was my intervention that made this part of the problem go away.  There was some up-grading from the standard Software Upgrader in between.  And the mouse is still jumping about, so the initial problem is not yet 'solved'.  I will continue, and try to replace the 14.04 with 14.10.

---

### Post by Pilot6 on 2014-12-05
upgrade to 14.10 won't help. You can just upgrade the kernel by

sudo apt-get install linux-generic-lts-utopic

Did you try another mouse?

---

### Post by logie on 2014-12-06
I did this and it worked in the terminal.  But the mouse is still jumping.
Also I got a message: "The volume Boot has only 10.8Mb disk space remaining." and suggesting I should free up some space.  I'd be glad if you could explain this and suggest action?
Again, thanks for your help so far.

I have tried various mice.  However the pointer jumps even if no mouse is attached.  The touchpad is also not working, which is why I'm dependent on the mouse.

---

### Post by Pilot6 on 2014-12-06
Regarding the space. Do you have /boot on a separete partition?
You can free some space by

sudo apt-get clean
sudo apt-get autoclean

And also you can remove old kernels.

Regarding the mouse. Did you try another mouse?

---

### Post by mörgæs on 2014-12-06
> **Pilot6 said:**
> 
And also you can remove old kernels.


Yes, sudo apt-get autoremove is likely to free a lot of space. Should be run once in a month.

---

### Post by logie on 2014-12-06
I think Boot is on the same partition as all the rest.
How would I remove old kernels?
I ran autoremove and the warning message has vanished.
I have tried various mice, but the pointer still jumps.  It jumps even if no mouse is attached.

---

### Post by mörgæs on 2014-12-06
You just did. Autoremove takes care of that - didn't you read its messages?

---

### Post by Elfy on 2014-12-06
> **logie said:**
> I think Boot is on the same partition as all the rest...

> The volume Boot has only 10.8Mb disk space remaining.

The error would suggest not - if you used lvm when installing you've got a seperate /boot partition.

Run 

```
df -h
```

See what that says.

---

### Post by logie on 2014-12-06
I ran the df -h  line  and I got a series of statements about size/use/available etc.  The key one is, I suppose

/dev / sda2       size 237M  used 214M  avail 11M  mounted on  Boot

The warning about lack of space is showing again.

Does this make sense, and what should I do now?

---

### Post by Elfy on 2014-12-06
> **logie said:**
> I ran the df -h  line  and I got a series of statements about size/use/available etc.  The key one is, I suppose

/dev / sda2       size 237M  used 214M  avail 11M  mounted on  Boot

The warning about lack of space is showing again.

Does this make sense, and what should I do now?

You would get the warning - you've got 11Mb left in there.

Remove old kernels - I tend to keep current and previous only.

---

### Post by logie on 2014-12-07
I do not know how to remove old kernels.  I have been advised to run 'clean and 'autoclean' but that did not work.  I opened my 'Boot' folder.  It had two folders 'efi' and 'grub' and six versions of each of three files:  one named 'abi ... generic', one named 'config ...generic' and one 'initrd.img ... generic'.  The last of these was the biggest, each copy about 20MB.

From this, I guess these are to do with various kernels, and I should probably be deleting them.

Is that the case, and how do I know which to get rid of?

---

### Post by Elfy on 2014-12-07
Clean and autoclean will only deal the apt cache - that is the packages you download when installing, packages that are updated. While it does decrease the space that / takes up, when you've got seperate partitions it won't always help - as you have found with /boot.

There are ways to clean up old kernels with the command line, but personally I find it easiest to use Synaptic ( a front-end to apt much like Ubuntu Software Centre) 

Install that - then run it from menu or hud or whatever you've got there (I don't use Ubuntu)

Once you've installed that and opened, select Installed in the Status section, then search in the search box for 3.13 then sort that by clicking on the Latest Version column.

You should then see all the kernel files you have sorted - right click on the oldest 4 or 5 with the SAME number and mark for complete removal. 

Screenshot shows what I've got - you'll not see exactly the same things - I'm running the dev version with a different kernel.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=258439&d=1417969990[/IMG]

---

### Post by logie on 2014-12-08
Many thanks for this.  I did as you say, and it worked: Boot now has plenty free space and no further warnings have come.

The mouse pointer still jumps, of course, but I can cope.

---

### Post by Elfy on 2014-12-08
> **logie said:**
> Many thanks for this.  I did as you say, and it worked: Boot now has plenty free space and no further warnings have come.

The mouse pointer still jumps, of course, but I can cope.

When you next get kernel updates - keep an eye on /boot :)

---

