---
title: "Asus M4N78 vs M4A78 help."
date: 2009-02-28
forum: Hardware
---

### Post by 4Foot on 2009-02-28
Hope someone can advise me. I had ordered a new Mobo, an Asus M4N78 Pro and when I went to pick it up they had shipped in the M4A78 Pro. 

As I understand it, the M4N has Nvidia GeForce 8 series chipset and graphics and the M4A has the AMD 780G chipset with ATI graphics. 

Both boards will do what I want but I read so much about problems with ATi and Linux that I am wondering if I should hold out for the M4N to arrive in a few weeks. 

I will use this with the Phenom II 940 CPU using the AM3 socket setup if that is any help.

I also assume that since AMD seems to be coming back to market with some good stuff that their incorporating their own graphics chips using their in house ATI products may be a safer bet.

Would be very grateful for any advice over ATI vs. Nvidea

Thanks

4Foot

---

### Post by Denbert on 2009-04-20
Hi there,

I'm looking for the exact same issue here in Denmark.

What was your conclusion?

---

### Post by 4Foot on 2009-04-20
> **Denbert said:**
> Hi there,

I'm looking for the exact same issue here in Denmark.

What was your conclusion?

Denbert:

I ended up going with the M4A78 mostly because the M4N78 was not yet released here in Canada and I did not want to wait.

This board and the Phenom 940 work pretty well together and it enabled me to put 8 gigs of RAM in my machine which is pretty useful when doing some video stuff.

I have to use the 64 bit version of Ubuntu to take advantage of the 8 gigs and I am currently running the Jaunty RC and liking it quite a bit.

On the video issue, I still think that the Nvidia solution may be better but I have not actually tried it so cannot tell. I do have some playback issues with almost every video player in the UBU repository, mostly jerky and quirky video playback with some synch probs trying Kaffiene and Movie Player. VLC has been choking up both the Jaunty Beta and the RC so I am hoping that the final release will fix that. 

Again, I am not certain if these issues are related to my use of the onboard ATI video component or just an issue with the 64 bit version of UBU.
 
I suppose I could buy and install an Nvidia card to see what happens but I am not tearing my hair out over it yet so will wait a while.

All in all I am happy with my Mobo CPU choice, very fast, quiet and stable. Love Asus and AMD, great bang for buck ratio as well.

Hope this answers your question. Good luck Denmark.

4Foot

---

### Post by Denbert on 2009-04-20
THANK YOU,

I'll order it right away with the same AMD - Phenom II X4 940 Black Edition CPU, as my need is a server with 64-bit OS and 8 gb RAM and NO gui.

How about networking and SATA - does it work with out a glitch, or did you do some "massage" under the installer?

---

### Post by grege on 2009-04-23
> **4Foot said:**
> Denbert

On the video issue, I still think that the Nvidia solution may be better but I have not actually tried it so cannot tell. I do have some playback issues with almost every video player in the UBU repository, mostly jerky and quirky video playback with some synch probs trying Kaffiene and Movie Player. VLC has been choking up both the Jaunty Beta and the RC so I am hoping that the final release will fix that. 

Again, I am not certain if these issues are related to my use of the onboard ATI video component or just an issue with the 64 bit version of UBU.
 
I suppose I could buy and install an Nvidia card to see what happens but I am not tearing my hair out over it yet so will wait a while.

Foot

Install the ATI fglrx drivers from the Ubuntu repositories and once up and running turn off Compiz desktop effects.

That should give you smooth video playback using xv.

If you use the Open Source driver you will need to manually edit /etc/X11/xorg.conf

Section "Device"
	Identifier	"Configured Video Device"
	Option "AccelMethod"	"exa"
EndSection

Which will give you good 2d desktop and xv video, but no 3d acceleration.

Good luck

---

### Post by 4Foot on 2009-04-23
Denbert:

I cannot help you with your networking question. I have never had much luck networking my Linux boxes with my Mac boxes and I don't have much need so mostly I just leave it alone and use "sneaker" network methods if I have to transfer files between machines. 

Don't really know what you mean by your SATA question however I have three SATA drives in this machine with no troubles. The board can handle 6.

Thank you Grege for your suggestion which I tried but my xorg statement includes a line " Driver fglrx" (sic) which your example did not and when I stuck in your example it didn't want to save, ( I think sudo was in order ) so I thought better of it and left it alone.

I did however find a fix for my jerky playback and relatively slow graphics. The MoBo has a default setting for Primary Graphics Controller of :

GFXO-GPP-IGFX-PCI

Where gfxo = pciexpress , gpp = gaming port , igfx = internal graphics and pci = pci card.

I changed the default to start with IGFX and my playback of video with all available players and codecs is perfect. It also worked with gpp set as default.

Makes perfect sense since I was and still am using the internal graphics.

I have tried this with the Proprietary ATI driver installed and without and they both work fine. Neither will allow me to utilise desktop effects but I personally don't care much about that so I am golden as is.

I hope this helps someone else.

Cheers

4Foot

---

### Post by punjabi_tt on 2009-04-27
hi,

I am also using the same config M4A78 Pro with AMD Phemon x4 940
but i could get my network going through onboard lan card.
Tried everything any suggestion will be appreciated. No Internet access.

---

### Post by Denbert on 2009-04-27
> **punjabi_tt said:**
> hi,

I am also using the same config M4A78 Pro with AMD Phemon x4 940
but i could get my network going through onboard lan card.
Tried everything any suggestion will be appreciated. No Internet access.

Which version of Ubuntu are you using?

I installed a Debian 5 Lenny 64-bit version - It had the NIC and therefore the installation worked perfect. I think you must have a "lenny" based ubuntu.

Or you could try the Debian Lenny netinst iso to check that the NIC is detected and work.

---

### Post by 4Foot on 2009-04-28
punjabi : 

I echo Denberts advice. I actually installed Fedora 10 on this system first and everything worked but the NIC. I concluded that Fedora could just not pick up the NIC so I tried Jaunty which had just come out in Beta and it worked perfectly so I have stayed with Ubuntu.

If you are already using Jaunty (9.04) then I am sorry I have no answer for you.

I also must give props to grege as his suggestion about turning off desktop effects is the key to eliminating jerky video playback.

Thanks grege.

4Foot

---

### Post by EXCiD3 on 2009-06-02
Have you guys had any issue with usb mice on these motherboards? Mine is the m4n version and after a little while it just stops working and requires a reboot. :( I can't figure out what is causing the problem yet either.

---

### Post by Denbert on 2009-06-03
> **EXCiD3 said:**
> Have you guys had any issue with usb mice on these motherboards? Mine is the m4n version and after a little while it just stops working and requires a reboot. :( I can't figure out what is causing the problem yet either.

Hmm, crazy.

I'll install a gui and a mice later this week, and report back.

---

### Post by EXCiD3 on 2009-06-06
Bleh, so I went to go install Hardy on my desktop in hopes that it would work fine with my M4N78...No dice. I cannot even get the Nvidia driver to install! :( I cannot find the chipset, and I'm using the latest driver with Hardy completely up-to-date too.

---

### Post by davemc on 2009-10-22
Solution here (usb vs graphics on same interupt)....

[http://excid3.com/2009/07/asus-m4n78-motherboard-usb-issue/](http://excid3.com/2009/07/asus-m4n78-motherboard-usb-issue/)

---

### Post by abhijeetkhapli on 2010-01-13
> **Denbert said:**
> THANK YOU,
 
I'll order it right away with the same AMD - Phenom II X4 940 Black Edition CPU, as my need is a server with 64-bit OS and 8 gb RAM and NO gui.
 
How about networking and SATA - does it work with out a glitch, or did you do some "massage" under the installer?
 
Even I need to install the desktop with 64bit but with 8 gb. would it support?

---

### Post by abhijeetkhapli on 2010-01-13
> **4Foot said:**
> Denbert:
 
I ended up going with the M4A78 mostly because the M4N78 was not yet released here in Canada and I did not want to wait.
 
This board and the Phenom 940 work pretty well together and it enabled me to put 8 gigs of RAM in my machine which is pretty useful when doing some video stuff.
 
I have to use the 64 bit version of Ubuntu to take advantage of the 8 gigs and I am currently running the Jaunty RC and liking it quite a bit.
 
On the video issue, I still think that the Nvidia solution may be better but I have not actually tried it so cannot tell. I do have some playback issues with almost every video player in the UBU repository, mostly jerky and quirky video playback with some synch probs trying Kaffiene and Movie Player. VLC has been choking up both the Jaunty Beta and the RC so I am hoping that the final release will fix that. 
 
Again, I am not certain if these issues are related to my use of the onboard ATI video component or just an issue with the 64 bit version of UBU.
 
I suppose I could buy and install an Nvidia card to see what happens but I am not tearing my hair out over it yet so will wait a while.
 
All in all I am happy with my Mobo CPU choice, very fast, quiet and stable. Love Asus and AMD, great bang for buck ratio as well.
 
Hope this answers your question. Good luck Denmark.
 
4Foot
 
Does all the hardware like lan and usb work fine?

---

### Post by Denbert on 2010-01-13
> **abhijeetkhapli said:**
> Does all the hardware like lan and usb work fine?

Yep - Works out of the box, running Debian Lenny 64 bit

---

### Post by 4Foot on 2010-01-13
> **abhijeetkhapli said:**
> Does all the hardware like lan and usb work fine?

Solved! I solved the video problem with the M4A78 card by disabling, ( or NOT enabling ) the Compiz Effects. I don't use them anyway so no biggie. But without effects enabled all videos play just fine in all players.

I use the 64 bit version of the OS because I like having the use of all 8 Gigs of Ram. Everything works just fine.

Cheers

4Foot

---

