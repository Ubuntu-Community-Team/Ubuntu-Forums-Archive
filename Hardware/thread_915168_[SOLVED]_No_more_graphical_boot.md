---
title: "[SOLVED] No more graphical boot"
date: 2008-09-09
forum: Hardware
---

### Post by rmmartins on 2008-09-09
Hello everyone! I'm new to all this (ubuntu and the forums).

Yesterday I had a normal graphical boot (the orange bar bouncing around and then the orange progress bar) but today, for some reason, the orange bar bounces around and then it goes into text mode (all those [OK]'s).

How do I get back to the orange progress bar? It's nothing really, but I just like the graphical boot more.

Thanks in advance and congratulations, this is definitely the best OS I've used in a while!

---

### Post by schmindy on 2008-09-09
You might have changed something:( Just restart it a couple times and you should be gtg:) Note: Do NOT do it all at once

---

### Post by rmmartins on 2008-09-10
Yes, well.. I did copy my whole 'home' from my old distro, and resized the partition through gparted (took 12 hours!).

But what exactly made it turn to text boot?

...

---

### Post by SoundFriend on 2008-09-10
I've two installs of Hardy and one always displays the messages from
"Reading files..." onwards, the other doesn't, and I can't find the difference in the configurations between the machines.

I'd like to turn off the text messages, is to do with the Grub configuration?

John :confused:

---

### Post by ice2921 on 2008-09-10
What display manager are you using? Depending on that you may need to reinstall the default display manager. Then reconfigure it through```
 sudo dpkg-reconfigure (gdm,kdm)
``` Or you can try cycling through the virtual displays F1-F7 until you get back to the GUI if and when you get to the GUI option it should tell you why you are able to launch the display manager.

---

### Post by caljohnsmith on 2008-09-10
> **rmmartins said:**
> Yes, well.. I did copy my whole 'home' from my old distro, and resized the partition through gparted (took 12 hours!).

But what exactly made it turn to text boot?

...
The fact that you did some repartitioning is what caused your problem I think; it's because when you repartition, some of your UUIDs can get changed. Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=828578&highlight=splash+screen](http://ubuntuforums.org/showthread.php?t=828578&highlight=splash+screen)

If you have any questions about it or need any details/info let me know; otherwise let me know how it goes.

---

### Post by rmmartins on 2008-09-15
Thanks caljohnsmith, it really seems to be the same problem...
I'm following your steps:

1. Make sure have the latest initramfs-tools - OK

2. sudo blkid - OK

Got:
/dev/sda1: UUID="6401d547-33c2-40df-82b1-4441d44996d8" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="5b46721b-327d-423c-aacc-60f8adad3893" 
/dev/sda5: LABEL="/home" UUID="4ad5a7e7-5d33-41d6-a602-614044b79497" TYPE="ext3" SEC_TYPE="ext2" 

3. Changed swap line UUID from /etc/fstab to match swap UUID from step 2. - OK

Now, the problems I had:

4. Changed UUID in /etc/initramfs-tools/conf.d/resume to match step 2.

>>> To match which UUID from "sudo blkid"? there's no "resume" type...

5. Changed /etc/uswsusp.conf to have UUID in step 2

>>> I've got no /etc/uswsusp.conf... do I create one? with what, exactly?

I've stopped here, I don't want to do anything stupid.

You help will be GREATLY appreciated..

Thanks!

---

### Post by caljohnsmith on 2008-09-15
> **rmmartins said:**
> 
4. Changed UUID in /etc/initramfs-tools/conf.d/resume to match step 2.

>>> To match which UUID from "sudo blkid"? there's no "resume" type...

I understand your confusion; the "resume" in that file refers to your swap partition, so just make sure the UUID in that file agrees with the UUID you got from blkid for your swap partition. 
> **rmmartins said:**
> 
5. Changed /etc/uswsusp.conf to have UUID in step 2

>>> I've got no /etc/uswsusp.conf... do I create one? with what, exactly?

No problem, if you don't have that file you don't need to create one; you can then skip that step. So once you correct the /etc/initramfs-tools/conf.d/resume file, just run:
```
sudo update-initramfs -u -k all
```
And you should be done. Let me know how it goes. :)

---

### Post by SoundFriend on 2008-09-15
Thanks, that worked for me :)

John

---

### Post by rmmartins on 2008-09-15
Perfect, it worked just fine!

Thank you very much!

---

