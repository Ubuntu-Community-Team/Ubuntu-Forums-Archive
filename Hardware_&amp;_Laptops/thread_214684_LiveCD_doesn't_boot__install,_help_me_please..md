---
title: "LiveCD doesn't boot / install, help me please."
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by Mischief on 2006-07-12
Hi fellas,

I ran into problems right away with Ubuntu.

I have a Acer Travelmate 8100 and I downloaded the Ubuntu CD 6.06 from the homepage and burned it to a CD.

When I reboot my laptop it takes me to the Ubuntu installer.
If i hit install I see the Unbuntu logo and I get these three lines:

Loading essential drivers	ok
Mounting root file system	ok
Moving mound points		ok
Adding live CD user

After that i see these lines:

PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2

[http://www.ubuntuforums.org/showthread.php?t=18701](http://www.ubuntuforums.org/showthread.php?t=18701)
"It required the acpi=off parameter before it would install."
Where do I put this line?

[https://wiki.ubuntu.com/LaptopTestingTeam/AcerTravelMate8103WLMi](https://wiki.ubuntu.com/LaptopTestingTeam/AcerTravelMate8103WLMi)
The install locks up if "linux noapic" is not entered at the boot prompt

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer)
Boot with 'noapic'. Modify xorg.conf as in model 1694. Patch the DSDT to have battery level detected.

I've searched the forum and the net and I've found some help.
The problem is that I don't know where to enter the information.
Do I change the parameters set when I hit F6?
I've tried to put the suggestions in the front, back and end but with the same result.

I've seen posts from ohter users with the same laptop who got it working.

Thanks for helping out!

Br.

//Mischief

(I posted a similar thread in beginners help but realized it was the wrong forum)

---

### Post by Mischief on 2006-07-13
Ok, I did some further testing.

First, I downloaded the DVD version instead.
After that I tried to put the following lines when starting from the CD.

acpi=off
noapic
nolapic
vga=771

I have no clue what exactly they do. They are however commands people used to get their system up and running.
 
>  Failed to start the x server. It is likely that it is not set up correcly. Would you like to view the x server output to diagnose the problem? YES NO

(EE) VESA(0):Set VBE mode failed.
Fatal server error:
ADDSCREEN/SCREENINIT failed for driver 0

> Would you like to view the detailed x server output as well? YES NO

Here I get pages and pages of information, unknown to me.
I guess there's something going on with my gfxcard (ati radeon mobile X700).

Depending on which of the acpi=off,noapic,nolapic, vga=771 i use I get different results. The most common one is that I will hear a chime, then nothing. Suddenly, if I put my ear to the laptop I can hear a drum going. I hit CTRL+ALT+BSPACE and see a lot of text and a command prompt. After that the whole tribe comes to play the drum, first one more drum and after that one more.

Any suggestions?

---

### Post by Zimmer on 2006-07-13
[http://ubuntuforums.org/showthread.php?t=213030&highlight=region+PCI](http://ubuntuforums.org/showthread.php?t=213030&highlight=region+PCI)

Seems the Sony user at the above thread cured some of his issues with a bios update...
..if that is of any help. I am searching for answers to this myself as I tried to boot several Live CD distros on a a friend's desktop and got similar warnings with them all . DSL just froze...

---

### Post by Mischief on 2006-07-13
Thanks for the reply.

I updated my BIOS 3-4 weeks ago, and I'm not aware of a never version.

What bothers me is that other Acer Travelmate 8100 users got their machines up and running. Don't want to give up on this just yet.

---

### Post by Mischief on 2006-07-14
Can someone please walk me through the LiveCD install process?

How long should it take? Do you hear chimes and drums? 
The extra options for installing, are those entered by pressing F6?
What extra options did you enter to get your system up and running?

I'm running out of thing to try here. Could it be that my laptop just isn't compatible with Ubuntu?

---

### Post by Mischief on 2006-07-16
It's been three days and I'm still not closer to get Ubuntu up and running. Hours and hours of rebooting, failing, searching rinse and repeat. How come nobody is able/want to help me out?

Am I asking in the wrong forum?

Is this problem totally new and unheard of?

Am I asking the question wrong, should I supply more information before posting?

Throw the dog a bone!

---

### Post by Hellkeepa on 2006-07-16
HELLo!

Post the contents of your "/etc/X11/xorg.conf" file, seems like something in there might be wrong. Hopefully someone who knows a lot about it will come by and notice it, if there isn't anything glaringly obvious that I can pick up on. :-P

Happy codin'!

---

