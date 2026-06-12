---
title: "Grub Error 15 in Stage 1.5 after upgrade to ext4"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by TimPy on 2009-05-30
Hi.  Recently, I decided to upgrade my drive to ext4.  So, I created another partition, copied my current partition over there (sudo cp -r -a) and then copied it back to my original partition after formatting.   

Now, when I boot up, I get: "Error 15" and it stops there.  Before, It says it is in stage 1.5.   I believe Error 15 is a file not found error.  I followed this [thread]("http://ubuntuforums.org/showthread.php?t=224351"): reinstalled grub (at hd0) and told it that root is at (hd0,0). 

I am completely lost as to what do now.  Is there a way I can tell Grub to be move verbose?   I would like to know what file it can't find, stuff like that.  I also need to make sure that I'm counting my partitions correctly... they are based on the physical location of the partition, and not the order created, correct?  

Any help/suggestions would be appreciated.  I want my Jaunty Jackalope back! :(

---

### Post by TimPy on 2009-05-31
Maybe some more information would help?

/boot/grub/device.map     contains
```
(hd0)     /dev/sda
```


I have followed [this thread's]("http://kubuntuforums.net/forums/index.php?topic=3081671.msg106228#msg106228") advice on the GRUB error 15 by running the commands:

```
sudo mkdir /media/fixthings
sudo mount /dev/sda2  /media/fixthings
sudo chroot   /media/fixthings
sudo update-initramfs  -u  -v
```

I can paste anything else that is relevant; just ask.  Can I please get some help?

And while I'm here....  Does anyone know how far in development [GRUB2]("http://www.gnu.org/software/grub/grub-2.en.html") is? It sounds pretty cool.

---

### Post by kruegger on 2009-05-31
This is not a Grub problem.
Grub does not find the Linux kernel headers and can't boot the pc.

You have copied your partition with a risky command for big files such as partitions. And after, you copied it back on a diferent file system. 

May I enquire why you decided to change your drive's file system?. What's wrong with ext3?. Is it compatible with ext4? 

Well, to confirm that your first partition copy is not corrupted, you should be able to boot from that partition by telling Grub. 
You know how: (hd0, (partition number-1)).

sudo fdisk -l to see your partition table. 

If it boots, not all is lost. If it doesn't...](*,) 

Another option, from live cd, mount that partition and explore it to check it . If you can open folders as usual it might be ok.

Again, sudo fdisk -l   -->to see your partition table.

sudo mkdir /media/fixthings

sudo mount /dev/sda[COLOR="Red"]x [/COLOR]/media/fixthings --> to mount sda[COLOR="#ff0000"]x[/COLOR] in fixthings

Be careful, you must know the partition you used to copy the original files (sda[COLOR="Red"]x[/COLOR]).

Sometimes you need to type this instead of the last command,

sudo mount -t ext3 /dev/sdax[COLOR="#ff0000"][/COLOR] /media/fixthings 

It will pop out an icon on your desktop you can click on and get into that partition.

When you need to work with directories or folders, you can use Nautilus graphically with root permissions

Alt+ F2 -->gksu nautilus  --> ctrl+H (to see hidden files) and then you proceed as usual with folder icons which can be partitions if you mount them first.
Another option, ran [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") from live cd. It is quite a reading but it is worth it. Take it easy.

If you like bleeding edge software (like Grub2 and beta prog.), learn to back up and _restore_ firstly. My advice. When you are learning, you need to touch everything.:biggrin:

Hope this help you

---

### Post by TimPy on 2009-05-31
kruegger: Thanks for the advice.   Next time, I'll be sure and backup my files more safely.   I normally do all my 'dangerous' stuff on a spare computer I have, so if anything bad happens, I have no worries.

I figured out the problem (With lots of help of course; thanks irc #grub).  It was a grub problem.  I had installed my system with 8.1 originally.  When I upgraded to ext4 however, the grub I was using was old and was not able to read off an ext4 partition.  I just needed to reinstall the latest version of Grub.  Now on to make this thread solved... however I do that.

One question though kruegger--  What should have been the proper way for me to upgrade to ext4? (I mostly did it cause I was bored....  I know) If you could point me to a good resource, I'll read it. (Otherwise I'll google for one.)  Thanks again!

---

### Post by Partyboi2 on 2009-05-31
> **TimPy said:**
> kruegger: Thanks for the advice.   Next time, I'll be sure and backup my files more safely.   I normally do all my 'dangerous' stuff on a spare computer I have, so if anything bad happens, I have no worries.

I figured out the problem (With lots of help of course; thanks irc #grub).  It was a grub problem.  I had installed my system with 8.1 originally.  When I upgraded to ext4 however, the grub I was using was old and was not able to read off an ext4 partition.  I just needed to reinstall the latest version of Grub.  Now on to make this thread solved... however I do that.

One question though kruegger--  What should have been the proper way for me to upgrade to ext4? (I mostly did it cause I was bored....  I know) If you could point me to a good resource, I'll read it. (Otherwise I'll google for one.)  Thanks again!
Hi, you can use
[http://blog.taragana.com/index.php/archive/upgrade-ubuntu-810-to-ubuntu-904-and-ext3-to-ext4/](http://blog.taragana.com/index.php/archive/upgrade-ubuntu-810-to-ubuntu-904-and-ext3-to-ext4/)
 as a guide. The process to convert to ext4 should not effect your data (no data lose) that is currently on the partition,  but in saying that its always good to backup important stuff before working on partitions.

---

### Post by kruegger on 2009-06-01
Nice to know you solved it.

Don't get me wrong. You did your research before upgrading, you went on it and something unexpected got in the middle. That's Linux when it comes to new "improvements", which I have grown allergic to. I stick to the well-known "world". I would not have done it better.;)

Only, I would have used dd to make the partition backup because it has proven slightly more reliable than cp. My hunch was that your backup was corrupted.

Sorry that I wasn't of help to you. I really meant it.:(

All the best

---

