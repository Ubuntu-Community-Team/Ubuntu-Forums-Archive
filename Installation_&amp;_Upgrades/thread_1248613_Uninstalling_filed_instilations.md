---
title: "Uninstalling filed instilations"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by RabbitWho on 2009-08-24
Sorry that should be failed not filed. 

I'm still left with the problem of how to get rid of the failed instillations of kubuntu. 

One of them is of 9.4 which I gave up on and the other is a 8.10 that I managed to.. and this is lovely.. delete my sudo password for. 

In the vista manager they're not named anything, there's (i think) 7 partitions now. It comes with a few already, and hopefully (if it worked) i made a separate partition for GRUB.. Is there anyway to identify all the partitions on the hard drive? 

And after i manage to get rid of those two extra kubuntu installs.. it sure would be cool if I could absorb that space back into this install of kubuntu...

downloaded filelight and here's some information: 



I'm confused now, it looks like the one on the bottom right is my current kubuntu install.. but the one on the top left should be


What I selected in the partition was &quot;use largest available free space&quot; So I can take it that it used the wrong space and that's why i'm seeing it's using 4 GB instead of 188

I'm getting fed up with all the bugs in Kubuntu anyway I think I'm ready to cut my losses and start again. 


I I'll resize it to take up just maybe 5 gigs and give its space to the new ubuntu installation.  

[IMG]http://img.photobucket.com/albums/v644/catharsisky/filelight-1.jpg[/IMG][/href]

Help?

---

### Post by cariboo on 2009-08-24
When you install Kubuntu, use the manual partitioning option to create new partitions for your installation. When using the manual option you can delete the old partitions and create new ones. Make sure you know which partition Windows is on so you don't accidently delete it.

---

### Post by RabbitWho on 2009-08-24
That wasn't an option when I installed 8.10

But anyway it will be with ubuntu?

How can i find out which partition is which? They have nothing written on them that makes any sense to me.   First time i deleted the extra partitions i deleted important grub files too. since then i've used a command which i was told gives the grub files their own partition.   So i really really need to identify partitions. Windows will tell me where it is and where its recovery partition is but i really need some way to identify the others.

---

### Post by RabbitWho on 2009-08-24
6, 7, and 9 are all named &quot;linux swap&quot; in g parted.  Don't know what that means one of is locked and it says active, the other two are not locked. Can I delete them?   1, 2, and 3 are probably vista   5 and 8 might be be the kubuntu i'm on now,,, or 8 and 9?  there's 5 megabites unallocated for some reason.   I can't figure out where the grub partition is if I really did make it.   I don't know what to make of this.    no help notes on the website...  [img]http://img.photobucket.com/albums/v644/catharsisky/gparted.jpg[/img]

---

### Post by RabbitWho on 2009-08-24
one last bump before i go to bed because it would absolutely rock if i didn't have to go deleting things willy nilly tomorrow.

---

