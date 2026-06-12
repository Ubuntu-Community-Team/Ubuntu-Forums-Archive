---
title: "LiveCD Ubuntu 9.10 Monitor frequency out of range"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by AliasOfiuco on 2009-10-30
I m trying the new Ubuntu 9.10, but the LiveCD gives me a frequency out of range issue when I try to use it or when I try to install the Ubuntu.
I tried the Alternate CD and I installed Ubuntu, but when I try to use it I have again the same problem. I looked around and I saw that I should start in recovery mode and then I should type:

sudo dpkg-reconfigure xserver-xorg
and so I did, but nothing..
It was supposed to ask me what kind of device I have and desired resolution.. but it didn't happen anything.
Can anyone give me a clue?
ThankYou!

---

### Post by abz1 on 2009-10-30
Same problem.

I have a Dell 2209WA, what monitor are you using?

---

### Post by AliasOfiuco on 2009-10-31
LG Studioworks 773N it's pretty old,but until now I didn't have any problem with it.

---

### Post by diggerOS on 2009-10-31
I'm experiencing the same thing myself. Tried also alternate cd with no good results. Never had this kind of issue with previous realeses, other distributions or windows installations. Someone pls help..

---

### Post by emigrant on 2009-10-31
im running jaunty,
and each time i boot the machine i get this message but after a few secs i get the login screen.

---

### Post by zebala on 2009-10-31
I just posted a thread about this but didn't know that it's the monitor's frequency that's out of range. I have this problem only with the alternate CD, but the normal works fine. The problem is I need to use the alternate install.

EDIT: I solved it by writing vga=771 as a boot parameter. Got it from the help menu.

---

### Post by AliasOfiuco on 2009-10-31
For zebala:
Could u pls just give me the link to this help menu u r talking about?
Thx.

---

### Post by Lockstar on 2009-10-31
I am having the same issue, tried adding vga=771 to boot comand line, no sucess.

Running on a Nvidia 7600GT, LG Flatron L1953T monitor

---

### Post by raven01 on 2009-10-31
i have the same problem except my monitor says the video mode is not supported. so i am very confused to why this would be. i have never once ever had a issue with getting ubuntu to run on this machine. and this goes back to version 6. and yes i have tried the alternate disk as well as safe graphics mode.

---

### Post by AliasOfiuco on 2009-10-31
To Lockstar:

Sorry I m a newbie, how can I add to boot comand line:
vga=771

---

### Post by Lockstar on 2009-10-31
When running the live cd, make sure that Try without making any changes option is highlighted.

press F6, a string of text should come up under all the options, then type vga=771

---

### Post by AliasOfiuco on 2009-10-31
@Lockstar

Thank you.

There you are a list of possible resolution:

vga=769 :640x480x256
vga=785 :640x480x32k
vga=786 :**640x480x64k**
vga=771 :800x600x256
vga=788 :800x600x32k
vga=789 :**800x600x64k** 
vga=773 :1024x768x256
vga=791 :1024x768x32k
vga=792 :1024x768x64k
vga=775 :1280x1024x256
vga=794 :1280x1024x32k
vga=795 :**1280x1024x64k**
vga=796 :1600x1200x256
vga=798 :1600x1200x32k
vga=799 :**1600x1200x64k**

---

### Post by Lockstar on 2009-10-31
Does anyone have a solution to this problem yet?

---

### Post by Lockstar on 2009-10-31
Ok tried using all of the vga=7xx codes, to no avail.

Now hoping that someone has a work around?

---

### Post by raven01 on 2009-10-31
i havent seen any solutions. so im basically just going to wait until a more stable iso comes out

---

### Post by Lockstar on 2009-10-31
Hopefully a stable iso comes out soon, the amount of problems people are having is quite large.

---

### Post by AliasOfiuco on 2009-10-31
I have found this in another forum:

il problema è l'uscita della scheda video; ho risolto con l'uscita digitale. se la tua scheda dispone di tale uscita usa il riduttore (da digitale a 15 del pin del monitor).
fai sapere se risolvi.

It says that: 
the problem is the output of the graphic card; I have solved it with the digital output. If your graphic card has that output use the adapter (from digital to 15 pins of the monitor).

I didn't try it yet.. if someone does it, pls let me know if it works.
Regards.

---

### Post by Lockstar on 2009-10-31
I will give it a go shortly,
hopfully will be posting results from Karmic liveCD

---

### Post by Lockstar on 2009-10-31
Success!!
I am currently posting this message from the Live CD Desktop.

So the workaround is to use the digital output from your video card and monitor. 

Good find [AliasOfiuco]("http://ubuntuforums.org/member.php?u=935271")

---

### Post by AliasOfiuco on 2009-11-01
I was glad I gave a useful workaround.
Thank you for giving me the feedback.
I will try it as soon as possible.
I will tag this thread as Solved!
Ciao. ;)

---

### Post by raven01 on 2009-11-01
i am using the dvi to vga connector on the box side. however, for some odd reason i cant seem to get a dvi to connect to the actual monitor. still havent figured out why pins are not lining up. but i still dont see why the system cant distinguish between the 2. will someone bug report this to the ubuntu devs so they can fix this?

---

### Post by Prince.Paul.K on 2009-11-01
Try 'Ctrl' + Alt + '+' to set the resolution...

It worked for me..!! :D

---

### Post by auanagana on 2009-11-01
> **AliasOfiuco said:**
> I was glad I gave a useful workaround.
Thank you for giving me the feedback.
I will try it as soon as possible.
I will tag this thread as Solved!
Ciao. ;)

ok.
ciao

---

### Post by dandnsmith on 2009-11-01
> **raven01 said:**
> i am using the dvi to vga connector on the box side. however, for some odd reason i cant seem to get a dvi to connect to the actual monitor. still havent figured out why pins are not lining up. but i still dont see why the system cant distinguish between the 2. will someone bug report this to the ubuntu devs so they can fix this?

Raven - I think you'll need to provide more data:
- which is 'the box' CPU?
- which sort of DVI (there are two, and some monitors will only handle the analog form). This may be why there is a pin mismatch (I don't know for sure, as I've only used the DVI connection on one CPU to monitor instance).

I've just got a (possibly useful) [description of types and connectors](http://www.interfacebus.com/Design_Connector_Digital_Visual_Interface_DVI_Bus.html) via google

---

### Post by AliasOfiuco on 2009-11-01
> **Prince.Paul.K said:**
> Try 'Ctrl' + Alt + '+' to set the resolution...

It worked for me..!! :D


Thank you for the tip! 
It worked for me too!
:D

---

### Post by abz1 on 2009-11-01
Thanks,

Using the vga=771 did not work, but switching my monitor to digital worked.

Hope this is resolved for other users.

---

### Post by dazcaz on 2009-11-29
Thanks to all for the solutions above. I had the same problem and was really getting fed up with it. A note for others when they say CTRL + ALT + + make sure that you use the + key on the number pad not the one above the = sign.... It took me a while to realise this.

I now have other questions which i shall ask on the forum.

Thanks again 

Darren

---

### Post by a3r0naut on 2009-11-30
On my AMD64 Emachine I got the vga=771 to work this way.

When Grub starts hit 'e' to edit. On the line with linux move to the end and after the word splash type "vga=771" without the quotes. 

Save and reboot and the video should come up as 800 by 600. Later you can change it to the resolution you want. 

BTW, frequency out of range is the monitor saying that the resolution set by the card is too high for it. You need  to either get a higher res monitor, use the digital input (as mentioned above) or reset the video card to a lower resolution (as in 771). 

It would seem to me that the default resolution on the 9.10 distribution should be set lower so people using older monitors don't have to deal with this issue.

---

### Post by B.Rizla on 2010-03-03
> **a3r0naut said:**
> BTW, frequency out of range is the monitor saying that the resolution set by the card is too high for it. You need  to either get a higher res monitor, use the digital input (as mentioned above) or reset the video card to a lower resolution (as in 771). 

It would seem to me that the default resolution on the 9.10 distribution should be set lower so people using older monitors don't have to deal with this issue.

I think you are mistaken (or just unclear about what you mean). It is not a resolution that the monitor cannot handle, it is the refresh rate that it cannot handle.

I have to rant...

Refresh rates and resolutions can be set independently under windows (admittedly my laptop only has 60hz as an option in Vista), so I suggest it is more appropriate to set it to around 60-70hz, as a fall back under ubuntu when a monitor is unidentified or info about what it can handle cannot be obtained (guessing a digital connection will allow this).

I am completely new to ubuntu, and when I did the 'try' option from the cd, to have a look before installing, my monitor (which is an old CRT on an analogue jack) tells me that 90hz is too high for it (something I am aware of; it is 10 or more  years old ffs!).

Judging by the numerous results google picks up on this subject, it does somewhat surprise me that nothing has been done to sort out the default refresh rate being a bit high for older equipment problem. It may be something that puts noobs off the OS too - Just like I decided to give up on LINUX some 10 years ago because of too many hardware (and driver) issues.

The resolution listing from AliasOfiuco on page 2 is handy, but meaningless to me without refresh rate info.
 
If there is a solution to setting a lower refresh rate on the command line, can someone post it?

I hardly think 'buy new equipment' is an answer. I may as well just buy a whole new desktop PC, bundled with an OEM of that world dominant OS and with a supplied LCD/LED monitor.

[SOLVED] yeah like fk it is!

(Oh and btw. my old IBM PS\2 keyboard is still going strong after 20 years of heavy use [not to mention a few cups of tea] :P)

---

