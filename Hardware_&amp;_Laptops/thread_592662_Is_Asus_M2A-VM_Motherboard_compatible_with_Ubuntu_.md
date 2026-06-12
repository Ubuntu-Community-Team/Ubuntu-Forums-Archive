---
title: "Is Asus M2A-VM Motherboard compatible with Ubuntu 7.10?"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by Uboontu on 2007-10-26
Hi, I am thinking of buying this PC ([http://www.jumbocomputers.ca/index.php?do=Product&cmd=pd&pid=000999&cid=812.167](http://www.jumbocomputers.ca/index.php?do=Product&cmd=pd&pid=000999&cid=812.167)). It comes with Asus M2A-VM Motherboard. Has anyone used this motherboard with Ubuntu 7.10? Are they fully compatible?

Thanks.

---

### Post by HOLOGRAPHICpizza on 2007-10-27
Yes, does anyone know? I'm looking into getting one of these motherboards too.

---

### Post by Uboontu on 2007-10-28
ok, i have bought a computer with this motherboard and has installed ubuntu gutsy on it. Everything seems to be working ok right now. I didn't encounter any major problems. I justed enabled the restricted ATI driver after installation and the display is ok. I still need to do more testing to see how compatible it is with ubuntu.

---

### Post by Deeta on 2007-10-28
I am using Gutsy 64bit Desktop on a M2A-VM HDMI as well :)

Safe for the Sound that is just 2-channel instead of 6 channel it works flawless :D
Yay :)

Is your sound output experiencing the same problems?

---

### Post by clavoie74 on 2007-10-28
I have this motherboard and I'm unable to install the ATI display driver, I'm stuck with a VESA generic.

When you say
> I justed enabled the restricted ATI driver after installation and the display is ok.
What do you mean exactly.  I'm new in Linux and Ubuntu and I'm not sure to understand.

Thanks for your help

---

### Post by hubfred on 2007-10-29
Hi,

greetings from germany. Nice forum, guys. I'll drop by more often :)

@Deeta

May I ask which BIOS Version you used in order to install the 64bit Gutsy? I also have the M2A-VM, upgraded to latest BIOS 1404.

I can install Suse 10.3 (32bit), but the setup of Ubuntu 7.10 doesn't even run, neither 32 nor 64 bit. After I press "install ubuntu" I can see five rows of protocol information and that's it. The setup gets stuck. I can press CTRL + ALT + DEL for rebooting. Everything else is only displayed in the prompt, but having no effect. HPET is off, so is ACPI (via command).

So, I'd kindly ask you to describe your current setting that works with Gutsy 64 bit. I can't wait to get it operating properly. Kinda wasted too many hours on this issue already.

Thanks in advance and take care y'all,
Kai

---

### Post by Deeta on 2007-10-29
@hubfred
Hiya, I have the same Bios version as you (1404).
Though an important difference might be that I use a 8600GT as GPU instead of the integrated X1250.

Furthermore I used the alternate install CD of gutsy instead of the live-install CD.
(I found the Feisty live CD's habit of defaulting to 1600x1200 at my Pentium3's 17"CRTvery annoying, so I made a wide berth around the Gutsy live CD)

If you have not done so yet I would give the Alternate Install CD a try :)

So long, and do not forget to Plug and Pray :)

---

### Post by Bill Currie on 2007-10-30
I have two systems with the Asus M2A-VM Motherboard one I use for a HTPC and the other is my primary system.  The Asus M2A-VM-HTMI Motherboard is in my primary system and works great with Ubuntu Fiesty and Gutsy, and Kubuntu 7.10. The other Home Theater system won't boot any of the above?? Hangs on boot with "Running Local Boot Scripts /etc/rc.local". The system is still running (keyboard to screen still active) but stopped.

Bill Gates did me the favor of shutting down my second copy of Vista and preventing the system from booting.  I made the decision to leave Mr Gates and move to Ubuntu. Spent one day finding libdvdcss etc. and now love it! I cannot believe how easy it is and how great the community support is.  THANKS

Now I have to get Ubuntu to boot on the HTPC. (The one with the registered copy of Vista).

---

### Post by kcbnac on 2007-10-30
> **Bill Currie said:**
> I have two systems with the Asus M2A-VM Motherboard one I use for a HTPC and the other is my primary system.  The Asus M2A-VM-HTMI Motherboard is in my primary system and works great with Ubuntu Fiesty and Gutsy, and Kubuntu 7.10. The other Home Theater system won't boot any of the above?? Hangs on boot with "Running Local Boot Scripts /etc/rc.local". The system is still running (keyboard to screen still active) but stopped.

Bill Gates did me the favor of shutting down my second copy of Vista and preventing the system from booting.  I made the decision to leave Mr Gates and move to Ubuntu. Spent one day finding libdvdcss etc. and now love it! I cannot believe how easy it is and how great the community support is.  THANKS

Now I have to get Ubuntu to boot on the HTPC. (The one with the registered copy of Vista).

If you installed the Server version, and its booting up to where it should display a login prompt, hit 'ENTER' - you'll see it.  Some random bug (I forget what causes it) makes it not display the login prompt.

My M2A-VM I ordered several months ago came with the original BIOS - I had to do a two-step upgrade, as one of the versions (around 0600) was when you could use the in-BIOS upgrade option - I had no problems installing Feisty or Gutsy, desktop or server, with this motherboard.  It currently (sadly) serves as my Windows gaming machine, though.

---

### Post by Uboontu on 2007-10-31
> **clavoie74 said:**
> I have this motherboard and I'm unable to install the ATI display driver, I'm stuck with a VESA generic.

When you say

What do you mean exactly.  I'm new in Linux and Ubuntu and I'm not sure to understand.

Thanks for your help

After your first boot, there should be a "restricted devices manager" icon on the top-right hand corner. Just click on that and choose "enable". It will set up the card for you.

---

### Post by Uboontu on 2007-10-31
> **Deeta said:**
> I am using Gutsy 64bit Desktop on a M2A-VM HDMI as well :)

Safe for the Sound that is just 2-channel instead of 6 channel it works flawless :D
Yay :)

Is your sound output experiencing the same problems?

I didn't really notice whether my sound is 2-channel or 6-channel, because i am using a pair of really cheap speakers.

---

### Post by Uboontu on 2007-10-31
> **kcbnac said:**
> If you installed the Server version, and its booting up to where it should display a login prompt, hit 'ENTER' - you'll see it.  Some random bug (I forget what causes it) makes it not display the login prompt.

My M2A-VM I ordered several months ago came with the original BIOS - I had to do a two-step upgrade, as one of the versions (around 0600) was when you could use the in-BIOS upgrade option - I had no problems installing Feisty or Gutsy, desktop or server, with this motherboard.  It currently (sadly) serves as my Windows gaming machine, though.

Could you briefly tell me how to upgrade the BIOS of this motherboard to the latest version? Thanks.

---

### Post by drbisio on 2007-11-13
Hi, I'm interested too.

How good are now the Ati graphic drivers for this board?

I've heard there is not support for xvideo extensions; 
However, is this mb capable of playing videos correctly (no stuttering and the like)?

bye

---

### Post by makeyre on 2007-11-15
I have no network support with this mainboard so I can't install restricted drivers, and it won't boot normally.

[http://ubuntuforums.org/showthread.php?t=609491](http://ubuntuforums.org/showthread.php?t=609491)

---

### Post by be4truth on 2007-12-08
Asus M2a-VM with Ubuntu 7.10 32bit

There are issues with this board:
First issue: When installing an error like this occurs 'cannot allocate resource region .....'
Solution: go into the BIOS and disable the HPET option. Use the 'Alternate Install CD 7.10'. Before installing pass the boot option 'acpi=off'. Make sure you floppy drive is either connected or disabled in the BIOS as the installation routine hangs looking for it.
After complete installation install the restricted ATI driver via restricted driver module. Resolution up to 1280x1024 is ok. Sound ok. Didn't had much time to test video. Will do soon.

---

### Post by ManiDhillon on 2008-01-21
> **Uboontu said:**
> ok, i have bought a computer with this motherboard and has installed ubuntu gutsy on it. Everything seems to be working ok right now. I didn't encounter any major problems. I justed enabled the restricted ATI driver after installation and the display is ok. I still need to do more testing to see how compatible it is with ubuntu.
Hey Bro are you able to switch to resolution of 1440X900, and are the videos playing fine?
Coz I have a 19" wide screen LCD and the above resolution don't play videos well on Ubuntu but that resolution run fine on Win XP.
I have ASUS M2A-VM with LG Wide Screen!

---

### Post by maverick340 on 2008-01-29
Does 6Ch sound work on an Asus M2A-Vm ? I am thiniking of taking this motherboard and i sue Ubuntu 7.10. I have Creative 5.1 speakers and I'd wish to use it. Can anyone please tell me if the surround sound works with this motherboard ?

---

### Post by Yellow Pasque on 2008-01-29
> **maverick340 said:**
> Does 6Ch sound work on an Asus M2A-Vm ? I am thiniking of taking this motherboard and i sue Ubuntu 7.10. I have Creative 5.1 speakers and I'd wish to use it. Can anyone please tell me if the surround sound works with this motherboard ?
I can't give you a definite answer, but I don't see why it wouldn't. The board uses a standard Realtek ALC883 codec. ALSA supports it with the standard hda-intel driver. You may need a later version of ALSA than the one that comes with Ubuntu 7.10 (ALSA 1.0.14).

---

### Post by maverick340 on 2008-01-29
Hmm and other than that ? Any other problems ?
I am buying this and i want to know is its compatible ..

---

### Post by jhboricua on 2008-02-08
I have this motherboard and recently installed Mythbuntu.  As others have stated, the integrated video card has no Xvideo support on the latest ATI drivers.

Sound is working great, I got the SPDIF bracket at eBay and configured Mythtv to use spdif out and it passes both DD5.1 and DTS signals just fine.

My problem now is video.  I use a DVI -> HDMI cable to my Samsung Slimfit HDTV.  The good part is after getting the modeline by runing "Xorg -probeonly", the picture comes up with no overscaning at 1280x720.  However since the ATI driver has no Xv support for the X1250 graphic chip on the motherboard, I have to use the opengl renderer option of mplayer.  That puts more stress on the CPU and I'm not able to play 1080p content, as it stutters from start.  I bought a cheap Nvidia 7200gs card and installed it and with it I get Xvideo support and can play 1080p content, but I get tons of overscan.

I've spent the last 3 or 4 days scouring on google, trying different modelines to no avail.  I can't get the the Nvidia card to output correctly on my HDTV screen.

So I took it out and went back to the integrated graphics, since the image dimensions are perfect and the opengl rendering is good for 99% of the video content I have.  I can only hope a future ATI release gives me Xv support.

---

### Post by maverick340 on 2008-02-09
i bought the asus m2n-vm DVI board a few days back. I am using an 8600gt card and 7.10 has drivers for it. However the onboard sound has a problem. I can seem to turn on 6ch sound  :(
Tried 7.10 and the development 8.04 both. No luck :( 
Can anyone help out ? 
btw the m2n-vm dvi has the nvidia 630a chipset.

---

### Post by Yellow Pasque on 2008-02-09
Your audio codec is a Realtek ALC662
Add/change the following sentence in the /etc/modprobe.d/alsa-base file.
```
options snd-hda-intel model=6stack-dig
```
Then I would try rebooting and after your system gets started, bring up amixer and see if you have any new channels.

---

### Post by maverick340 on 2008-02-09
Thanks temujin , I ll try this and let you know soon :) (maybe even an hour ;) )

---

### Post by Yellow Pasque on 2008-02-09
[SIZE="4"]Updated 6/6/08 for ALSA 1.0.17rc1[/SIZE]

Here are the scripts to build ALSA 1.0.17rc1 from source.

Make sure you go to System -> Administration -> Software Sources and have the first 4 repositories enabled (also make sure the CD is disabled unless you have a slow internet and would prefer to use the older versions of the packages on the CD). When you close that dialog, Ubuntu will ask you to update your software sources. Make sure you don't have Update Manager or Synaptic Package Manager open and click yes/ok to update the package list.

Now save these files to your desktop, and:
```
cd ~/Desktop
sudo chmod 777 alsa_1.sh
sudo chmod 777 alsa_2.sh
sudo sh ./alsa_1.sh
```
Then reboot, and when the system comes back, run:
```
cd ~/Desktop
sudo sh ./alsa_2.sh
```
Also, make sure your alsa-base file is configured correctly:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

You may need to reboot again after running the second script before the sound will work.

**Remember** to unmute any new channels in alsamixer.

---

### Post by maverick340 on 2008-02-09
Yea, i just installed ubuntu 7.10 (i had 8.04) and installed the latest version of alsa (1.0.14)
You sure those scripts will get the surround sound to work. And its it removable later on if i want to try some ohter method ..

---

### Post by tjk on 2008-02-16
> **Temüjin said:**
> Actually, before you do what I suggested above, I would recommend updating to the latest version of ALSA. I've got some scripts that make it real easy for you. Just save theses files to your desktop, and:
```
cd ~/Desktop
sudo sh ./alsa_1.sh
```Then reboot, and when the system comes back, run:
```
cd ~/Desktop
sudo sh ./alsa_2.sh
```

I've tried numerous things to get ALSA working again.  I ran your first script and rebooted (some terminals failed to open after I did this), and then I ran the second script, which resulted in the following terminal output:
XXX@XXX:~/Downloads$ sudo sh ./alsa_2.sh
[sudo] password for XXXXXX
cp: target `/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko' is not a directory
cp: omitting directory `/lib/modules/2.6.20-15-generic/kernel/sound/'

It appears that something didn't work.  Can you help me out?

---

### Post by selwynpolit on 2008-02-18
I have the same board (ASUS M2A-VM with AMD Athlon X2 BE-2300) and I installed the AMD 64-bit version of Kubuntu 7.10.  I'm a bit scared of installing the ATI drivers.  When I tried that it made my video go away and I had to completely reinstall linux.  

Does anyone have a recommendation as to where to go to get better video drivers than the default ones?  Perhaps I should just accept those?

thanks for your thoughts
Selwyn

---

### Post by Yellow Pasque on 2008-02-18
The open-source radeonHD drivers are going to be the best 2D drivers for the integrated 690G chipset. If you really need 3D/Compiz acceleration, you're stuck with fglrx/Catalyst and you have my deepest sympathies. See my sig for info on installing radeonHD.

Also see [http://groups.google.com/group/x1250](http://groups.google.com/group/x1250) for info on how to install Catalyst and set up the xorg.conf

---

### Post by MrGreen on 2008-03-10
tried script but alsa_2.sh reports no such files or directory can you help ... hda is missing pci ?

Thanks 

MrG

---

### Post by Yellow Pasque on 2008-04-15
I've updated the instructions above because a lot of people were having problems with the first script not working. For some reason, Gutsy has the needed software sources disabled by default and the first script would fail to build the modules, causing the second script to fail and no sound. If you tried the scripts and still have no sound, follow the instructions about Software Sources and try again.

---

### Post by David2926 on 2008-04-19
I have installed ubuntu 7.10 on the M2A-VM motherboard and was doing great until I tried to install the Linux driver from the DVD. 

Notes on installation - do not use a SATA DVD drive for installation, use a PATA or USB drive for installation. After installation there should not be a problem with the SATA DVD drive! Also I have not been able to use the Restricted driver manager with the ATI video drivers. I down load the driver from the ATI site. Note the M2A-VM has the Xpress 1250 chipset and it is different from the Radeon X-1250 card, be sure to get the correct driver. Also you may need to run the aticonfig --initial command. I have to add the dual-head option to get my two monitors to work.

Now to the sound problem. The defult installed sound driver worked, it was just that the volumn level was less then expected and when I tried to install the linux driver from the DVD it uninstalled the driver then failed to compile the new driver. The post from Temujin has given me some ideas to try.

---

### Post by jocko on 2008-04-19
> **David2926 said:**
> Note the M2A-VM has the Xpress 1250 chipset and it is different from the Radeon X-1250 card, be sure to get the correct driver.

Even if the cards are different, they use exactly the same driver. ATI only makes one driver, which supports all cards from radeon 9500 and better, except perhaps the absolutely newest models.
The version of fglrx in the gutsy repos claims to support the [FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2]Radeon Xpress 1250 IGP, which is the only ati chipset or card I can find with "1250"[/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT] in their name, so there's no need to download the newest drivers from ati (dual screen and xvideo support is pretty much broken on the newer drivers, making it a pain to try to watch a movie through tvout...).

---

### Post by David2926 on 2008-04-19
Interesting!  And it looks like you are probably right. Looks like I downloaded the 8.3 version just before the 8.4 update. 
But my problems with the restricted manager goes back to Feisty and an ATI X1600 card. When I enabled the restricted driver I lost internet access! But I downloaded and ran the ATI script and with a little tweaking got my dual monitors working. 
I did a clean install of Gusty on the M2A-VM.  The versa driver was limited to 640 or 800 screen res! An the restricted driver would not recognize the chipset. Again I got the ATI driver, did an aticong &#8211;initial=dual-head and all is working great. I have a Dell 18&#8221; on the DVI and a NEC 17&#8221; on the VGA, both at 1280x1024. I have not tried TV out.

---

### Post by Deeta on 2008-05-11
Edit: Seems Hardy is able to correctly do 6ch after all :) upon hunting down my old settings from gutsy it was possible to unmute all 6 channels and enable 6ch mode in alsamixer.

Has anyone succeeded to get their 6channel sound working with their m2a-vm as of yet?
(It didn't work in gutsy and even now on hardy with Alsa 1.0.16 it does not work :-/)

---

### Post by erginemr on 2008-05-12
@Temüjin,

Thanks a million. Thanks to your marvellous installation script, quite a few people have easily updated their ALSA to the latest version. I am suggesting your scripts (with credit to you of course) to anyone having problems with ALSA detecting their sound card.

Regards,

Emrah

---

### Post by Dogmeat Jack on 2008-05-15
I have had some success with hardy(8.04) and sound on the M2A-VM.
The answer is along the same lines as Temüjin, but with a different model.
Simply edit the /etc/modprobe.d/alsa-base files and add/change the line:
```
options snd-hda-intel model=3stack-6ch-dig
```
To test run the following command:
```
speaker-test -Dplug:front -c6
```

---

### Post by bixejo on 2008-05-28
> **Temüjin said:**
> Here are the scripts to build ALSA 1.0.16 from source.

[...]


Hi, Temûjin.

Thank you for posting these scripts to make us easier the ALSA driver installation.

I haven't tried them yet because I'd like to make you one question before. When I compiled 1.0.15 (which is no longer working after some update of linux-ubuntu-modules) I remember that in the driver ./configure step I also added the following options:

```
--with-cards=hda-intel --with-sequencer=yes --with-oss=yes

```Some people recommended also:

```
--with-kernel=/usr/src/linux-headers-$(uname -r)
```, but I didn't put that option and 1.0.15 worked great for me till this damn update.

Are these options no longer needed/useful/advisable?

By the way, in the case it's relevant I'll drop here the errors I'm getting right now when I try to load the snd-hda-intel module:

> 
[  849.552868] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[  849.552879] snd_hda_intel: Unknown symbol snd_ctl_add
[  849.552958] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[  849.552962] snd_hda_intel: Unknown symbol snd_pcm_new
[  849.553042] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[  849.553047] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  849.553119] snd_hda_intel: disagrees about version of symbol snd_card_register
[  849.553123] snd_hda_intel: Unknown symbol snd_card_register
[  849.553189] snd_hda_intel: disagrees about version of symbol snd_card_free
[  849.553194] snd_hda_intel: Unknown symbol snd_card_free
[  849.553253] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  849.553258] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  849.553325] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[  849.553329] snd_hda_intel: Unknown symbol snd_card_proc_new
[  849.553548] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[  849.553553] snd_hda_intel: Unknown symbol snd_ctl_find_id
[  849.562617] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[  849.562629] snd_hda_intel: Unknown symbol snd_ctl_new1
[  849.562767] snd_hda_intel: disagrees about version of symbol snd_component_add
[  849.562772] snd_hda_intel: Unknown symbol snd_component_add
[  849.562853] snd_hda_intel: disagrees about version of symbol snd_card_new
[  849.562857] snd_hda_intel: Unknown symbol snd_card_new
[  849.563976] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  849.563985] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  849.564072] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[  849.564077] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  849.564144] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[  849.564149] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  849.564286] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[  849.564380] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[  849.564440] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[  849.564445] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  849.564521] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[  849.564527] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[  849.564615] snd_hda_intel: disagrees about version of symbol snd_device_new
[  849.564620] snd_hda_intel: Unknown symbol snd_device_new
[  849.564716] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[  849.564721] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  849.564816] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[  849.564821] snd_hda_intel: Unknown symbol snd_card_disconnect
[  849.564881] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  849.564886] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  849.565207] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[  849.565212] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  849.565270] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[  849.565275] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
Thank you very much for all you efforts and time,

---

### Post by Yellow Pasque on 2008-05-28
bixejo, I recommend upgrading to Ubuntu 8.04 which has ALSA 1.0.16 with PulseAudio, or switching to OSS4 (see sig).

I'm not an ALSA expert because I don't like/use it, but I'll try to help you to the best of my ability.

You can use the --with-sequencer=yes flag. In fact, the documentation recommends it: [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)  I've never heard of the other flag. If you want oss compatibility, install the oss-compat and alsa-oss packages.

---

### Post by bixejo on 2008-05-28
> **Temüjin said:**
> bixejo, I recommend [...]
 
The idea of upgrading to 8.04 just makes me shiver... It's just a few months ago since I got my laptop fully working with 7.10 after a helly long time of fighting with some drivers like the ATI proprietary driver and also the ALSA sound, so the idea of beginning again with all this causes me a headache. But if in a short time I don't succeed in making sound work again I shall consider it.
 
Thank you anyhow for your efforts in helping us to depend a little less on Windows, which actually is the only reason I keep on fighting against all these problems.

Edit: I solved my problem. I found the key in the second script posted by Temüjin (file alsa_2.sh) (sorry buddy, I ran out of words to say thank you more times!)

---

### Post by kzlazy on 2008-06-22
Would just like to thank Temüjin as the scripts solved my sound problem.

Thanx a lot

---

### Post by agentbond007 on 2008-06-27
I have had the M2A-VM for a while now. Tried to install Ubuntu properly for some time but the 3D acceleration graphics would not work. 2D ATI was working, but as soon as I would enable 3D the screen would hang in dark mode after restart.

So finally I decided to buy an 8800GT for my other computer and take the 7300LE and put it into the M2A-VM computer. Installed Unbuntu 8.04 thinking that the Nvidia card would solve all driver issues I was having before. However, the screen would still turn black after enabling the 3D accelartion drivers and restarting.

Finally, I read some posts and decided to update my system BIOS to the newest ones....1705. On the very next restart, I enabled the 3D drivers and it works well now. So, I am guessing the issue was with the outdated BIOS that were not properly compatible with 3D acceleration in Ubuntu. I have not tried taking out the Nvidia card and enabling the ATI drivers, so I can not say if the BIOS update will solve any issues with onboard graphics. So if you are having trouble with the 3D onboard graphics, updating the BIOS might be something try, but no guarantees.

---

