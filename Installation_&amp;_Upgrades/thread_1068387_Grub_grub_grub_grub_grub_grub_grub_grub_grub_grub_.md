---
title: "Grub grub grub grub grub grub grub grub grub grub grub grub grub grub grub grub grub"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by The Staucher on 2009-02-12
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB............and I am stuck -no boot 
and Unbuntu 8.10 never boots anymore. Also I tried installing windows Vistax32 Ultimate, and I get a disk error. However, Ubuntu's Live CD boots ok. And I spent all day on multiple hard drives. I am thinking maybe God hates me more than the other guy - LOL - but OK Not really. Here is low down, I am new to the Linux thing, about a week into it. Trying to configure multiple hard drives, saving my media (160GB), installing, reinstalling trying things out and finding better ways to do it. Well, I have been using Gparted to format and partition drives in about everyway possible (I learned a lot and "LOVE" Gparted so far.) I have probably partitioned 20 times and have installed vista and ubuntu 5 or sicks times today alone.
And I tried it a couple times with one hard drive in at a time with the TB and the 160 GB.

System Details:
1 TB sata
160 GB Sata
250 GB IDE
37GB Raptor SATA
4 GB Ram
2 8500GT Nvidia cards
3800+ AMD-64 x2

And if I have ruined all my hard drives I will shoot myself.... in the foot LOL

And it's funny, I finally fingered out how I wanted to configure everything and this happens. Like I said, I only have been dabbling in Linux for a week or two. I do say, minus all this, I love it.

-Nubi1Kenobi

---

### Post by gabo.cr on 2009-02-12
Do you want to do a dual boot ?

---

### Post by mttman on 2009-02-12
It seems like you want to dual boot so here's what i suggest. Get all the data you want to keep onto one fat32 partition on the 1TB drive,Then nuke every other partition (every partition except the one with your data on it that is) and start from scratch. then install Windows how you want it, then install ubuntu how you want it and set up your mounting when you install ubuntu. I think it's possible that all the resizing in Gparted might have caused data corruption so salvage what you can. if you can still see your drives running under a live cd, and see the data on them then there's about a 75% chance it's just the 1's and 0's that are screwed up and reinstalls should fix it. otherwise i hope you have good warranty's and your data is government sensitive.

Just some standard practice info (not necessary):
/boot goes on a 100MB ext2
/ goes on a however big ext3 - this has to be ext3 i think

also keep in mind that you can only have 4 partitions on a HDD without using extended partitions which get to be a headache when your new to this stuff. so basically try not to make more then 4 partitions to one drive

Something that i think but am not sure of :
your bootloader needs to be on your master drive

Hope this helps

---

### Post by The Staucher on 2009-02-12
Yes I put the boot loader on the master drive
Check it out,
I want to multi-boot, and I planned on having another flavor and/or Vista 64 also. However, the GRUB issue was a result of me starting over. I got all my data on the 250GB hard drive and removed it. I left the 160 TB in and zapped it with Gparted-live. Checked the bios and it was ok, proceeded with the windows vistax32 installation. 
When the install did its first reboot it gave me a disk error, so I did the install a couple times, zapping the partion and formatting with both the windows installer and Gparted-live. So, is said F* it and grabbed my 64 bit Ubuntu disk and the Live session booted. I installed it to the 160, rebooted to the grub grub grub and it would not load. So I said F* it again and put the TB hard drive in by itself, gparted it (hehhehe I love it), installed windows vista to the same effect. and the same thing with grub happened when I installed it again.

*Is it possible that I may have ruined all my drives, I cant see that happening because they wouldnt all fail at once, some of them are 4 or 5 years old, and the TB drive is brand new.

*Half the time my bios locks up (its old 2005), but it is a different problem - What is it I am missing here?


-Nubi1Kenobi

---

### Post by mttman on 2009-02-12
It could be a problem with your Disk drive controller which means new motherboard. it would make a little sense because of how much stress it's been put on today especially if your boards from 2005. try to use one drive to install and put in a few different places, different plugs. also make sure that you have the drive set on master (as in check the jumpers) hope thats what it is

---

### Post by The Staucher on 2009-02-13
Thanks for your help, I saw another issue very similar to mine. The explanation they got for the screen-full of grubs was mutiple linux installs and grub being misdirected or something. I checked all the wires and connects, I am good, and I pray its not another motherboard -;) however this could be an excuse for me to upgrade -----dont tell my wife she hates me spending money on pc stuff hehehehe.

---

### Post by caljohnsmith on 2009-02-13
Getting a repeated "GRUB" written across your screen at start up can often be due to how your HDD is set up in BIOS. But first, in order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by The Staucher on 2009-02-14
Make a long story short, I fixed it and need to modify my boot loader I think.

I left the TB hd in and the raptor, I set up 4 partitions on the TB, 1 was for vista, 2 was for "/", and 3 was for "/home". I setup the small tiny raptor drive for SWAP.

I installed windows, it had some problems, no matter how anything was setup i kept getting a response from the installer saying it need to install its volume and there was room on the raptor. This angered me. So I disconnected it (after I powered it off, lol). Restarted  and let vista have the whole TB disk, the install was flawless from the as far as I could tell. I rebooted and it was good. Ok...the raptor got hooked back up and.....

So thats all fine and dandy grabbed my Gparted live disk, resized the vista partition, and added 3 more. It corrupted the windows boot loader as I suspected. I repaired it with the windows disk and tested a reboot and proceeded to install Ubuntu. It went well  and updated, rebooted a couple of times. 

Now, I can not boot my Vista. after I select it "Starting Up" with a blinking curser under it.

For sh!ts and giggles, i did this and to my surprise and lack of experience, I wasnt surprised at all and was forced to consider going to sleep. I rebooted into Ubuntu and did this in the terminal.

bryan@bryan-desktop:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/bryan/Desktop/boot_info_script*.sh: No such file or directory
bryan@bryan-desktop:~$ 


hrmmmmmmmmmmmmmm
-Nubi 1 Kenobi

---

### Post by grantcentral on 2009-02-14
Can you give an idea of how and where you want to layout ubuntu and windows?
Also give an idea which drives are internal and external? Finally, give us an idea where the install of ubuntu is failing.

TO start out, it is easier to install Windows first. Grub handles the install better if other O/S is already in place.

---

### Post by The Staucher on 2009-02-15
I want to setup a dual boot.

Both drives are internal.
I have 4 primary partitions on the TB hard drive. and the only partion on the tiny raptor drive is my swap area.

my first partition is vista, second is storage, third is my /root and the last is my /home.

I installed vista first. The used gparted to resize and make all my partitions. doing that corrupted my windows loader. So I put in the disk and "repaired" vista. It worked. So I installed Ubuntu, and it works. Now when I select vista/longhorn option from grub, i get the "Starting Up" with a blinking curser under it.

Ideally I would like to boot windows vista or ubuntu whenever I want with minimal effort. just like if I reboot I can just pick which ever one I want.
-Nubi 1 Kenobi

---

### Post by AlexBellisBrown on 2009-02-15
My eyes are bleeding with the ammount of times ive seen the word GRUB on this page... :)

---

