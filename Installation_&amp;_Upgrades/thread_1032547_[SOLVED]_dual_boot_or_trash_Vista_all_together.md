---
title: "[SOLVED] dual boot or trash Vista all together?"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by niceguy123 on 2009-01-06
I've got a new loptop with vista pre-installed. I've been trying to dual boot ubuntu for the past couple of days with no success. 
Someone here showed me a link with a how-to install unbuntu on a vista machine, I went though the first steps there calling for "shrinking" the disk via vista. The next stage would be rebooting with the live ubuntu cd and choosing the partition that was created in the shrinking process. The problem is that even after creating the partition I am not being given the option to choose a partition. I run the live cd, it shows the ubuntu splash screen, and proceeds upto choosing the installation language. After that the screen goes dead and nothing happens. I've tried this numerous times with new ubuntu and kubuntu 8.10 disks and also tried with with older 7.10 installation disks. All the same. no progress. Is it possible to get vista and ubuntu dual booting or do I need to format the disk and run unbuntu without the vista all together?

---

### Post by vgrisham on 2009-01-06
I'm about to dump Vista completely, but I've been dual-boot for over a year without problems. 

There IS an option to choose the partition; I don't have the install CD with me. I'll try to fire it up tonight and note where that step is.

EDIT: I just re-read your post. You're right to have installed Vista first. That's the way I did it, and Ubuntu automagically found it after I shrunk the partition.

---

### Post by logos34 on 2009-01-06
have you tried the text-based Alternate install CD?

---

### Post by donkyhotay on 2009-01-06
If you have never used linux before, continue trying to dual-boot. Despite how good it is not everyone likes linux and some go back to windows. I always recommend dual-booting or doing a wubi install if you're just experimenting with linux. On the other hand if you've used linux before, are pretty comfortable with it, and are only dual-booting because you might want it to satisfy your gaming fix or something... dump vista and don't look back.

---

### Post by Mark Phelps on 2009-01-06
Sorry for what might be a "dumb" question -- but when you created the partition for Ubuntu, did you create an Ext3 format partition, or NTFS?

AFAIK, Ubuntu can't install to an NTFS partition --which might explain why the installer doesn't see the partition.

---

### Post by vgrisham on 2009-01-06
> **Mark Phelps said:**
> Sorry for what might be a "dumb" question -- but when you created the partition for Ubuntu, did you create an Ext3 format partition, or NTFS?

AFAIK, Ubuntu can't install to an NTFS partition --which might explain why the installer doesn't see the partition.

Hopefully he didn't create a partition at all--that takes place during the Ubuntu install. The correct order of operations for this kind of install is to first shrink an existing partition in Vista (leaving it as unformatted space). He'll then target that empty space as his locale for Ubuntu's install.

---

### Post by niceguy123 on 2009-01-06
> **vgrisham said:**
> Hopefully he didn't create a partition at all--that takes place during the Ubuntu install. The correct order of operations for this kind of install is to first shrink an existing partition in Vista (leaving it as unformatted space). He'll then target that empty space as his locale for Ubuntu's install.

That sounds right. And I took a look again in vista computer management, the new area is classified as unallocated. But, as I said before, when I run the ubuntu disk, before it reaches the stage where I would choose the partition the screen dies.   

I have been using Ubuntu as my main OS for nearly a year and a half. I don't need vista for security. The only thing is that I have had some tools that I have not found linux solutions for like magicjack phone plug and some banking website. Firefox 3 might has solved some of those websites problems, I haven't yet checked each one. And for voip I might just stick to skype and forget about magicjack.

---

### Post by thk123 on 2009-01-06
I am running a dual boot Vista/Ubuntu. When I installed Ubuntu (computer came with Vista) I just stuck the disk in, booted from that and there was an option to choose the relative size of partitions etc. all from within the installation. I didn't do anything in Vista and I am not an advanced user, there was a nice drag and drop slider. I was using 8.04, so it might be different for 8.10 (but I can't think why)

---

### Post by niceguy123 on 2009-01-06
> **thk123 said:**
> I am running a dual boot Vista/Ubuntu. When I installed Ubuntu (computer came with Vista) I just stuck the disk in, booted from that and there was an option to choose the relative size of partitions etc. all from within the installation. I didn't do anything in Vista and I am not an advanced user, there was a nice drag and drop slider. I was using 8.04, so it might be different for 8.10 (but I can't think why)

I've been having the same problem with 8.04 on this vista box.

---

### Post by Shazaam on 2009-01-06
When the livecd first boots hit F4 for boot options, then choose "Safe graphics mode" and see if it will let you finish the install.

---

### Post by vgrisham on 2009-01-06
> **niceguy123 said:**
> That sounds right. And I took a look again in vista computer management, the new area is classified as unallocated. But, as I said before, when I run the ubuntu disk, before it reaches the stage where I would choose the partition the screen dies.   

I have been using Ubuntu as my main OS for nearly a year and a half. I don't need vista for security. The only thing is that I have had some tools that I have not found linux solutions for like magicjack phone plug and some banking website. Firefox 3 might has solved some of those websites problems, I haven't yet checked each one. And for voip I might just stick to skype and forget about magicjack.

Well, I'd bet a valuable part of my anatomy that you've got a bad download and/or burned cd. If I were you, I'd download it again and give it another go. 

As for the applications that you feel you may need to have from Windows, you might want to post in another forum for alternatives. I only keep Vista around to work with my scanner for the once in a blue moon that I need it. That's about to change though as I'm getting a newer more penguin friendly scanner soon.

---

### Post by niceguy123 on 2009-01-08
Thanks to Shazzam I was able to get past the place I was stuck in 8.10 installation. I tried it this time with Kbuntu. Haven't done that before and it was a little strange. Although I did install on a new partition I still destroyed the vista installation because I choose to make the windows partition smaller from within the ubuntu installer.

I couldn't figure out how to add a regular gnome desktop over KDE so I tried reinstalling Ubuntu, 8.10 continued to give me the same problem as before a blank screen in the middle of the installation. But I did succeed in installing an older ubuntu 8.04 but there I couldn't figure out how to tie in to wireless Internet. I tied into a wired Internet and ran the update manager. That was good for the applications but did nothing for Ubuntu.

Again I tried the 8.10 and succeeded in installing 8.10 on the full partition.

No more MS on this computer. I feel like I pulled a bad tooth.

---

### Post by meindian523 on 2009-01-08
If you installed Kubuntu fine,but have problems with Ubuntu,the best place to look is at the ISO.It might be a bad burn and/or a bad ISO.Check the md5 sum of the ISO,and burn at the lowest speed possible.And to upgrade from Ubuntu 8.04 to 8.10,go to System>>Administration>>Software Sources(may be different in Kubuntu)>>Updates and change release upgrade to show normal releases.Now you can upgrae to 8.10.This problem occurs because 8.04 is a LTS release,and by default LTS releases upgrade only when there's a new LTS release.
And to install a GNOME environment in Kubuntu,just ```
sudo apt-get install ubuntu-desktop
``` in konsole.

---

### Post by vgrisham on 2009-01-08
> **niceguy123 said:**
> 

I couldn't figure out how to add a regular gnome desktop over KDE so I tried reinstalling Ubuntu, 8.10 continued to give me the same problem as before a blank screen in the middle of the installation. 

It's really easy to install one or both desktops. If you're running Gnome, pop into a terminal and code:
> sudo apt-get install kubuntu-desktop

If you're running Kubuntu, in a terminal code:
> sudo aptitude install ubuntu-desktop

Then log out. When you log back in, choose which session (KDE or Gnome) that you want to run. You may find that your gnome menus get flooded with kde applications and vice-versa, but this is easily cleaned up by right clicking on the Applications menu and editing your menu entries.

[Here]("http://www.psychocats.net/ubuntu/index") is a great website that I referred to heavily when starting out.

Good for you for pulling that tooth. Enjoy.

---

