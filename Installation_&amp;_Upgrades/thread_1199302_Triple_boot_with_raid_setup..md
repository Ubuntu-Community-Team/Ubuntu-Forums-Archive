---
title: "Triple boot with raid setup."
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by Justin2240 on 2009-06-28
Hi all I'm new to the whole Linux crowd but I'm wanting to learn a lot about it so that I can be verse in Windows and Linux.... The problem that I'm having is that I have one hard drive that is a Seagate 250g 7200rpm (this is the one that I'm running Linux in). I have 2 other hard drives that are raided together. They are both 250g 7200rpm Hitachi's. On these seperate hard drives that are raided together I have Windows XP Pro 64x on one partition and then I have Windows 7 on another. I was wanting to know how to make Linux the main boot loader between all 3 OS's. Can anyone help me out??

---

### Post by running_rabbit07 on 2009-06-28
System/ Administration/ Synaptic Package Manager. Search for StartUp-Manager, install it. 

Then open it from the Administration Menu and in the Boot Options tab you will see the Default Operating System, click on which ever system you prefer to load and then when you start the PC it will go to the boot loader menu.

 If no button is pressed after 7 or 8 seconds the boot loader will load the OS you selected in from the StartUp-Manager menu.

---

### Post by Justin2240 on 2009-06-28
I went into synaptic manager and I couldn't find "startup-manager" I even tried going to "terminal" and typed in "sudo apt-get install startup-manager" and that didn't work. Is there another way to get it???

---

### Post by running_rabbit07 on 2009-06-28
It should be there. As soon as I finished typing start, it was there. o into it again and click reload then try again.

 You can also do the search with out the "-" in it, that may help. 

I have 8.04 and 9.04 running on 2 PCs and StartUp-Manager was there on both.

---

### Post by Justin2240 on 2009-06-29
Ok will try it again when I get home today. For some reason tho I feel that it will come to the same result. Will update on situation after 6 o clock today.

---

### Post by running_rabbit07 on 2009-06-29
I just had a thought. (there goes the world) I don't know if you had tried to find the startup-manager in the Add/Remove menu, the program isn't in that menu, just checked.

---

### Post by Justin2240 on 2009-06-29
Wait do you mean that the "startup manager" ISN'T in the add/remove programs menu?

---

### Post by running_rabbit07 on 2009-06-29
No, it (StartUp-Manager) is in the Synaptic Package Manager. You will find Synaptic under the System/ Administration menu.

---

### Post by Justin2240 on 2009-06-29
Oh ok I got kind of mixed up with the last post that you left. Anyways I know where synapatic is but what about Kgrubeditor can that get the job done too. If so can you explain how I can do it??

---

### Post by running_rabbit07 on 2009-06-29
I installed kgrubeditor to check it out and it does not work with Ubuntu.

When I clicked to start the Kgrubeditor it wouldn't start, it tried but closed.

It is for KDE or Kubuntu. 

If you can get the StartUp Manager installed from the Synaptic Package Manager I can walk you through the changes no problem. If you can't find it anywhere then I don't know of anything else.

If anyone else looks at this and has any other advice, feel free to share.

[URL="http://www.freeporndumpster.com/show.php?l=0927179&f=screenshotsynaptic_package_manager_.jpg"]
[/URL]

---

### Post by running_rabbit07 on 2009-06-29
I do want to apologize for the site I used for posting the screenshots.

If there is a non-porn site that anyone knows of for free image hosting, please email me.

I fell like a dumb @$$. I previously didn't notice the attachment icon in the post screen.

---

### Post by Justin2240 on 2009-06-29
Yeah I was about to say man I could get into alot of trouble with looking at that site cuase Im at work right now lol.

---

### Post by running_rabbit07 on 2009-06-30
Did you get it to work?

---

### Post by Justin2240 on 2009-06-30
Sorry I have been away for a bit I'm still working on it. Been running back and forth with all the different OS's that I have. Will update my progress later on tonight.

---

### Post by Justin2240 on 2009-07-02
Ok to go into more of an in depth eplination of what I had done before I installed Linux Ubuntu I had first had Linux Kubuntu on the hard drive that I had installed Linux Ubuntu on. Then I had installed Ubuntu and I think thats y I was able to install synaptic manager on there. Now Im not able to install startup manager and I think that is partly y Im not able to triple boot with my other operating systems.

---

### Post by running_rabbit07 on 2009-07-02
If Synaptic Package Manager is not installed due to a corrupt OS install you should probably reinstall Ubuntu into that partition. But when you do you should use gparted from while booted into your live disk and reformat the partition that way it is clean when you reinstall Ubuntu. That way everything functions properly.

How is Windows 7 treating you? Is it better than Vista? Being Vista turned out so badly they should have kept up support for XP longer until the market for Seven had time to work.

 I was mad when I took my CompTIA A+ classes just to find out that the books didn't cover Vista and there was yet another OS getting ready to release. Of coarse I started Network+ this summer and I found out Mike Meyers had a new release for that book last month and we aren't using it.

---

### Post by Justin2240 on 2009-07-03
Ah dude windows 7 is freaking awesome man. It has the same look as windows vista but it has the functionality of XP. It still takes about a gig to run the OS depending on weather your computer is high end or not (and Ive only heard this from other people but apparently it only takes a gig to run the OS if your computer is like TOP END) but all and all the OS is really stable and seems to have no bugs or gliches at all. Im running it right now and I put a few games on there and they work great. I also heard that they brought in Linux developers (which they are not any more) to do software developement for Windows 7. You can also see where that applys too if you mess with some of the windows on your desktop.

---

### Post by handyguy on 2009-07-03
> **running_rabbit07 said:**
> I installed kgrubeditor to check it out and it does not work with Ubuntu.

When I clicked to start the Kgrubeditor it wouldn't start, it tried but closed.

It is for KDE or Kubuntu. 

If you can get the StartUp Manager installed from the Synaptic Package Manager I can walk you through the changes no problem. If you can't find it anywhere then I don't know of anything else.

If anyone else looks at this and has any other advice, feel free to share.

[URL="http://www.freeporndumpster.com/show.php?l=0927179&f=screenshotsynaptic_package_manager_.jpg"]
[/URL]

are you sure kgrubeditor doesnt work i have ubuntu jaunty 9.04 and it works perfectly try 
sudo apt-get install kgrubeditor it always worked for me

---

