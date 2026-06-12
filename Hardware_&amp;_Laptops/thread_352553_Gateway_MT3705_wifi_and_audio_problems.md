---
title: "Gateway MT3705 wifi and audio problems"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by sil40dori on 2007-02-03
Hey all- I'm kinda a nux noob, i haven't used it in years so go easy on me =)

Anyway, I just bought this laptop from bestbuy (599 + free scanner/printer!) and installed Ubuntu 6.10 (Vista FTL!). Everything seems to be working fine except there is NO audio and wifi seems to be half working or something.

lspci entries are:

Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8185 (rev 20)

The are 2 audio devices listed under the volume control- HDA ATI SB (Alsa mixer) and Sigmatel STA9200 (OSS mixer) and neither of them work. I did a bit of research and I believe the chipset is Sigmatel but they do not provide drivers directly so...?

The wifi on the other hand is weird. Network Manager displays wifi networks in the area but doesnt display signal strength and cant connect to them (even unsecured ones) and also doesn't seem to support WPA at all.

Any help is appreciated! Thanks

---

### Post by wykedengel on 2007-02-14
I have the same model computer and the same problems. Being that the computer is still fairly new (hit the shelves between Dec 2006 and January) there is not a lot of support for this model yet. I love Ubuntu, but need these functions to work. Can anyone help?

---

### Post by kmicic on 2007-02-14
To get wireless to work, use ndiswrapper + original realtek WinXP drivers (rtl8185L). I don't have sound working yet, but might give it another try this weekend. Feel free to check my notes for updates:

[http://gvshoot.com/html/modules/wiwimod/index.php?page=notebook-mt3705](http://gvshoot.com/html/modules/wiwimod/index.php?page=notebook-mt3705)

---

### Post by sil40dori on 2007-02-16
Well, eventually, somehow I got the wifi halfway working. It wouldnt display correct signal strength but it would connect to my home wifi network with just MAC filtering, but I suppose it would have worked with WEP..no WAP though. I tried ndiswrapper and it got a bunch of errors.

Audio...I must have tried everything in the book to get this working, but I just cut my losses and threw Vista back on, I love listening to music so it was hell to not have sound working.

I think the sound has something to do with routing the amp or something. I could play things in xmms fine and it would look like its playing but no sound...

This laptop was a steal for the price, but I really wish it had cardbus and not express54....

---

### Post by wykedengel on 2007-02-20
sil, like you, i got wireless working, but sound is still an issue. i was able to install xp (for the time being) and hunt down xp compatible drivers. i will see if i can get the drivers to work on ubuntu and report what i came up with.

---

### Post by kmicic on 2007-02-21
wykedengel,
where did you find XP sound drivers?

---

### Post by Amorfish on 2007-02-26
I have the Gateway MT3705 too, and I'm very new to linux and ubuntu.  I managed to install the driver for wifi with ndiswrapper and I was hoping that this thread would generate a solution for the sound card problem.  

How do we know what driver is needed?  I set up a dual-boot with Vista and Device Manager in Windows calls it "High Definition Audio Device" with drivers mfd by Microsoft.  Pretty vague, huh?  I hope one of you guys is doing better than me on this...

But meanwhile I'm happy to report that my Logitech USB speakers were recognized by ubuntu and that they work -- god i love plug-n-play.  

Well, they work most of the time...  If I unplug them and then plug them in again, there's a good chance they won't work until I reboot.  Also if I use Amarok, then close it, and then open the built-in video player, I get an error message saying that the "audio output device is busy." 

So sometimes it doesn't work.  

And sometimes it just works.  Sometimes.

---

### Post by wykedengel on 2007-02-28
the XP drivers that are compatible with the MT3705 can be found here:

[http://support.gateway.com/support/drivers/search.asp?param=MX3702+&st=kw](http://support.gateway.com/support/drivers/search.asp?param=MX3702+&st=kw)

both the MX3702 and MT3705 share the same bios, and so the drivers are compatible. I am running XP now until I can get everything up on Ubuntu. I am not a fan of windows, but i am also not a fan of having a computer that i cannot use.

---

### Post by gpv on 2007-03-12
Anybody found a solution to the sound problem.Please help..

---

### Post by calnev on 2007-03-17
I too own an MT3705 Gateway Laptop and having the exact same problem. I tried to reload ALSA as was described in this post [http://www.ubuntuforums.org/showthread.php?t=314564&highlight=gateway+sound](http://www.ubuntuforums.org/showthread.php?t=314564&highlight=gateway+sound) but to no avail.

I picked up a pair of "Logitech Stereo USB Headset 250". Purchased at Fry's Sunnyvale for $39.95.The sound quality on this headset is really good and they work great with Amarok and Skype.

Anyway it's good to have sound and now I can start loading all my music in Linux and say bye bye to Windows and iTunes soon! I am SO happy to get rid of Vista... such a disappointing o/s.

I do hope though someone can figure out the driver issue. It would be nice to be able to use the built in sound card as a backup at least.

---

### Post by Kyral on 2007-03-18
I find this very interesting. Mainly because I also just got a MT3705 and was wondering WTF. But mainly because of the reroute...I wonder what caused it. Oyah this isn't specific to Ubuntu, I'm running Arch and the same thing is happening...

Anyway someone should email the ALSA guys...

---

### Post by lvleph on 2007-03-19
I decided to do away with Windblows once again. I too have the MT3705. However, my wireless worked imediately without any real fuss. All I ended up doing was going into
Administration>Networking and activated the wireless connection, changed the setting for my specific network (ie ESSID and Key) then clicked on the network icon in the upper right. In there it had lo, so I changed that to wlan0 and it connected.

Afterwards, I noticed there was an easier way. Just skip the admin portion go straight to the network icon in the top right. Type in wlan0 and press configure, now you can enter your essid and key. 

However, if your wireless is using WPA there probably will be more things that need to be done. The wireless I connect to is WEP so... I have no control over my wireless and so I was very glad nothing had to be changed with the wireless network.

As far as sound goes, I am still trying to figure that one out.

---

### Post by lvleph on 2007-03-21
The problem with the sound is actually alsa. There is already a bug report for this. They have fixed the problem with STAC9250, but we have STAC9200 and they are still working on that.

Here is the discussion about it:
[http://www.ubuntuforums.org/showthread.php?t=314564](http://www.ubuntuforums.org/showthread.php?t=314564)

---

### Post by CMB_TEXAS on 2007-03-30
Hello everyone!!!! I have had the same problems with the Gateway MT3705 audio drivers. The preloaded Vista crashed two months in so naturally I loaded XP pro. Got everything but the audio until today. Thanks to a freind of a friend who knows someone at Gateway, we have finally solved this problem. Just follow this link and run this driver, your sound should be up in no time.

[http://rapidshare.com/files/23581042/D00560-002-001.exe](http://rapidshare.com/files/23581042/D00560-002-001.exe) 

Good luck.

---

### Post by nvydis on 2007-04-14
exe file doesnt work on ubuntu.

---

### Post by LMelior on 2007-04-24
About a week ago I spent several hours trying without success to get audio to work on my MT3705, right down to modifying patch_sigmatel.c and recompiling.  I even downloaded the [STAC9200 data sheet]("http://www.idt.com/?genID=STAC9200") and double-checked that all of the node IDs matched the ones in the file.  

The only thing I really added to patch_sigmatel.c was in this section:

```
static struct snd_pci_quirk stac9200_cfg_tbl[] = {
	/* SigmaTel reference board */
	SND_PCI_QUIRK(PCI_VENDOR_ID_INTEL, 0x2668,
		      "DFI LanParty", STAC_REF),
	/* Dell laptops have BIOS problem */
	SND_PCI_QUIRK(PCI_VENDOR_ID_DELL, 0x01b5,
		      "Dell Inspiron 630m", STAC_REF),
	SND_PCI_QUIRK(PCI_VENDOR_ID_DELL, 0x01c2,
		      "Dell Latitude D620", STAC_REF),
	SND_PCI_QUIRK(PCI_VENDOR_ID_DELL, 0x01cb,
		      "Dell Latitude 120L", STAC_REF),
	SND_PCI_QUIRK(PCI_VENDOR_ID_DELL, 0x01cc,
		      "Dell Latitude D820", STAC_REF),
	SND_PCI_QUIRK(PCI_VENDOR_ID_DELL, 0x01cd,
		      "Dell Inspiron E1705/9400", STAC_REF),
	SND_PCI_QUIRK(PCI_VENDOR_ID_DELL, 0x01ce,
		      "Dell XPS M1710", STAC_REF),
	SND_PCI_QUIRK(PCI_VENDOR_ID_DELL, 0x01cf,
		      "Dell Precision M90", STAC_REF),
	
	// Added 4-15-07
	SND_PCI_QUIRK(0x107b, 0x0318,
		      "Gateway MT3705", STAC_REF),
	
	{} /* terminator */
};
```

Which was suggested in [this ALSA bugtracker thread]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2814").  I just changed the vendor ID and device ID to match ours.  I also got the LFE mixer item but it didn't help.

That's about as far as I got.  There is another section in patch_sigmatel.c right above the part that I posted about pin configurations, but I couldn't find anything similar in the datasheet to check it against.  Also, in the data sheet, it says this:> Note: All widgets in this document are applicable to theSTAC9200/9200D B1 Revision. For widgets pertaining to the STAC9200/9200D A1 Revision, see STAC9200/9200D Datasheet Revision 0.8.
I don't know if we have the older revision or not, but I can't find that version of the data sheet anyway.

I just thought I'd bring these things up in case anyone decides to have a look for themselves.  In the mean time I just bought [these USB headphones from Newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16826106150"), which I am quite happy with.  They feel a little flimsy but they sound awfully good to me (I'm no audiophile though).


EDIT:  
I just had a more thorough look at the data sheet and the source file, and I think I see where the pin configurations come into play.  But, I don't know enough to determine whether something should be changed, or if they even have anything to do with our problem.  For instance, on page 66 of the data sheet it shows the "Digital In" (SPDIF In) pin configuration.  The one in patch_sigmatel.c seems different, but I can't really tell, and if it is different, it's probably supposed to be that way since the data sheet only seems to give possibilities.

---

### Post by dracflamloc on 2007-05-06
If you comment out the bottom two blacklists in /etc/modprobe.d/blacklist you can get your wireless working fine with the open source drivers for RTL8185.

Weird bug though when you enter your SSID enter it with an EXTRA letter at the end. Seems theres a bug where it chops off the SSID by 1 character.

I really wish I could get this sound to work

---

### Post by chocolatetoothpaste on 2007-05-07
> **dracflamloc said:**
> If you comment out the bottom two blacklists in /etc/modprobe.d/blacklist you can get your wireless working fine with the open source drivers for RTL8185.

Weird bug though when you enter your SSID enter it with an EXTRA letter at the end. Seems theres a bug where it chops off the SSID by 1 character.

I really wish I could get this sound to work

I tried this, and it recognizes my hardware, it even brings up a bunch of networks to connect to, but when I try connect (to mine), it gets to 28% (configuring), and either gives up, or crashes.  not sure what that's all about.  Working on the problem right now, will post updates.
In the meantime, does anyone else have any ideas?

---

### Post by nsholland on 2007-05-18
The audio driver can be found at: [http://support.gateway.com/support/drivers/getFile.asp?id=20598&dscr=Sigmatel%20Audio%20Driver%20Version:%205.10.4946.0&uid=159771792](http://support.gateway.com/support/drivers/getFile.asp?id=20598&dscr=Sigmatel%20Audio%20Driver%20Version:%205.10.4946.0&uid=159771792) 

The wifi driver is at: [http://support.gateway.com/support/drivers/getFile.asp?id=20799&dscr=Realtek%20Wireless%20LAN%20Wireless%20Network%20Driver%20version%205.1060.0413.2006&uid=159770957](http://support.gateway.com/support/drivers/getFile.asp?id=20799&dscr=Realtek%20Wireless%20LAN%20Wireless%20Network%20Driver%20version%205.1060.0413.2006&uid=159770957)

All other drivers are at: [http://support.gateway.com/support/drivers/search.asp?st=pn&param=2905898R](http://support.gateway.com/support/drivers/search.asp?st=pn&param=2905898R)

Drivers you need: 

D00584-001-002.exe - Realtek Wireless LAN Wireless Network Driver version 5.1060.0413.2006
D00516-002-001.exe - Marvell Network Driver Version: 8.50.1.3
D00671-001-001.exe - ATI Chipset Driver version: ATI 5.10.1000.7
D00620-001-001.exe - Realtek Media Card Reader Driver version: 2.0.9.3 
D00670-001-001.exe - Agere Modem Driver version: 2.1.72
D00669-001-001.exe - Synaptics Touchpad Driver version: 8.3.7.0
D00680-001-001.exe - ATI Video Driver version: 8.283

D00560-002-001.exe Sigmatel Audio Driver Version: 5.10.4946.0

These drivers also work for the MT3707

---

### Post by yayme on 2007-05-19
I have a MT3707 and can't get the sound or wireless networking working. Any suggestions?

---

### Post by Ziox on 2007-06-13
Bump! A friend of mine also has the MT3705 and We had tried for several weeks trying to get Audio and Wireless. Could someone please provide a comprehensive guide to enabling wireless and/or sound?

Thanks in Advance.

P.S.  If I remove the drivers from the blacklist, I can receive all the wireless networks, however they are all at 0% and connecting to anyone of them fails horribly.

---

### Post by asetSDU on 2007-06-22
Hi, i have same problems. But im using both XP and Vista. VistaBootPRO_3.3.0.2.exe helped me:)
Advice same;)

---

### Post by Ziox on 2007-06-23
I've done more research and of course these problem driver issues.  Windows drivers do not work on linux, so thanks for the advice, but it won't help.  

As for all the linux users.  The wifi problem can be solved by installing ndiswrapper and applying the correct windows .inf file.  However, you must also make sure that ndiswrapper module loads into kernel at start up. To add it on startup:

gksudo gedit /etc/modules

append ndiswrapper to the end of the file.

save and reboot.

Now to the problematic audio.  As far as I know, even the most recent version of alsa will not fix the problem.  So there is no use compiling ALSA.  In other words, we, as non-developers/coders, cannot do anything about the sound.

However, I have heard that if you have an USB-based speaker, you can hear sound from the USB - strangely enough...I haven't tested this method yet, so I cannot confirm this.

---

### Post by asetSDU on 2007-07-06
i have only image of C: where evrysing is allright, it working..
Manufacturer: SigmaTel
Model: STAC 9200: 5.10.5082.0
but icouldn't find them..
so if somebody could find them it would be better..

---

### Post by asetSDU on 2007-08-15
Yes i got it!!!!!!!!!!!
Audio drivers....:guitar:

---

### Post by kwszola on 2007-08-22
If anyone has the audio drivers or a solution to get Ubuntu to have sound with this laptop please post it.

---

### Post by brandoncolorado on 2007-08-24
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

Same problem I think.  Well known, unfixed.

---

### Post by asetSDU on 2007-08-28
> **kwszola said:**
> If anyone has the audio drivers or a solution to get Ubuntu to have sound with this laptop please post it.
how can i share them ????

---

### Post by birdsixone on 2007-09-07
So do you have sound working on that model of laptop now? What audio drivers did you use and where did you find them at? Reply or send me an email at [email]birdsixone@yahoo.com[/email].

---

### Post by Master_Z on 2007-09-09
Bump. I have this laptop too and it sucks not having sound and wi-fi. Songs look like they are playing yet I cant hear them, not even through headphones. As for wi-fi, it shows my AP but I can never connect.

---

### Post by imaho85 on 2007-09-11
Hi, I'm new to all this but I finally got my sound to work on my gateway mt3705 for feisty.  If anyone is interested I used the patch from this [[COLOR="Blue"]link[/COLOR]]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036").

---

### Post by Shoadow56 on 2007-09-13
You absolutely sure this works? Cause it seems like a lot of people have been having trouble with this, as have I. I had to go and install XP because I didn't have sound and was very dissapointed by the whole thing.

I just don't want to go and have my heart broken on the matter. :'(

---

### Post by imaho85 on 2007-09-13
haha yea, I know how you feel.  I just got the sound to work a couple of days ago after almost a year without sound.  So far everything is still working.  I found the link I posted above from [[COLOR="Navy"]here[/COLOR]]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948").  They talk about the patch on the comments toward the bottom.

---

### Post by amarrero on 2007-09-16
Follow this link:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

It was submitted a patch for alsa version 15rc1 that makes the sound work in laptops Gateway MT3705.

---

### Post by chocolatetoothpaste on 2007-09-17
sorry if I sound dumb, but how exactly do I use these patches to get my sound working?  and when will this patch be merged to the main project?

---

### Post by birdsixone on 2007-09-17
How do we apply the patches? I can't find a tutorial on it.

---

### Post by imaho85 on 2007-09-18
Like I said I'm new to this, so this probably isn't the proper way to do it, but this is how I got it to work.  btw I'm using the 15rc1 drivers so I don't know if the 15rc2 drivers work.

go to:
[[COLOR="DarkOrange"]ftp://ftp.silug.org/pub/alsa/driver[/COLOR]]("ftp://ftp.silug.org/pub/alsa/driver")
download:
alsa-driver-1.0.15rc1.tar.bz2

go to:
[[COLOR="DarkOrange"]ftp://ftp.silug.org/pub/alsa/lib/[/COLOR]]("ftp://ftp.silug.org/pub/alsa/lib/")
download:
alsa-lib-1.0.15rc1.tar.bz2

go to:
[[COLOR="DarkOrange"]ftp://ftp.alsa-project.org/pub/utils/[/COLOR]]("ftp://ftp.alsa-project.org/pub/utils/")
download:
alsa-utils-1.0.15rc1.tar.bz2

go to:
[[COLOR="DarkOrange"]https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036[/COLOR]]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036")
download:
patch_sigmatel.c.patch-1.0.15rc1-simple
15rc1_patch_install

make sure they are all in the same folder and then cd to the folder and type
sudo sh 15rc1_patch_install

then you might need to reboot for it to work

---

### Post by chocolatetoothpaste on 2007-09-18
thanks for that guide imaho.  I hope to get my sound up and running soon.  For anyone interested, I found these while surfing the net:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L)
They are the drivers for the RTL8185 wifi card.  I tried to compile them, but got errors, so I'm posting the link to see if anyone wants to take a crack at debugging.  Let us know if you figure something out!

These ought to make quicker work of it, for anyone who is lazy like me, just paste this into the terminal:
```

wget -P ~/downloads/alsa ftp://ftp.silug.org/pub/alsa/driver/alsa-driver-1.0.15rc1.tar.bz2; wget -P ~/downloads/alsa ftp://ftp.silug.org/pub/alsa/lib/alsa-lib-1.0.15rc1.tar.bz2; wget -P ~/downloads/alsa ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2

```Then you still have to get the patches from ALSA.  Hope this makes someones day just a little easier!



Hey everyone!  I have an update!  I was able to get my WIFI working!  if anyone else has had issues with this, let me know and I'll post the instructions I followed tomorrow.  Otherwise, I hope everyone else is successful in getting their mt3705's working right!  I am having issues with ALSA, but hopefully they will iron out.

---

### Post by dannyh7 on 2007-09-22
Good  news.  If you use vmware player and the kubuntu 7.0.4 appliance (available on vmware's website under appliances) the sound for the MT3705 works automatically.

---

### Post by Shoadow56 on 2007-09-25
chocolatetoothpaste, can you post how you got your WiFi working? I've been trying everything and I have gotten it to work once in the past, but not cannot seem to get it working again. *NDISwrapper* will install the drivers for the device, but then it won't do anything else. And *ndisgtk* won't even register the hardware is installed when I use that.

---

### Post by chocolatetoothpaste on 2007-09-26
> **Shoadow56 said:**
> chocolatetoothpaste, can you post how you got your WiFi working? I've been trying everything and I have gotten it to work once in the past, but not cannot seem to get it working again. *NDISwrapper* will install the drivers for the device, but then it won't do anything else. And *ndisgtk* won't even register the hardware is installed when I use that.

sure thing!  First, follow the directions on [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"). When you have that working right, do:
```

sudo apt-get install wifi-radar

```I found that if you connect to an unsecured netowrk KNetworkManager (I use kubuntu) will connect, but if you connect to a secured network, for some reason it won't connect.  Wifi-radar will connect though.  I use WEP encryption with a hex key, and I was able to connect just fine with wifi-radar.  I'm not sure what wifi-radar is doing to make it work, though I wish I knew.  I like editing files myself rather than letting a gui do it.  Anyway, this is all I did, and I have reproduced it several times, so if it doesn't work for you, I'll be quite surprised.  Hope this helps!

---

### Post by Shoadow56 on 2007-09-26
Oh, and btw, did you ever get sound working? Since I couldn't get my wifi working I've been trying to get sound working. I really hate .tar.bz2 files, they took me forever to figure out and when I did, I found out that I had already decompressed them. So atm I am trying to install the ALSA patches. What about you?

---

### Post by abridge on 2007-09-26
My internal wireless card sucks. It never connect to school network and connect to my network for several hours then stop.  what type of wireless adaptor the laptop takes? thanks

---

### Post by Shoadow56 on 2007-09-27
What do you mean by wireless adapter, you mean what kinds of other cards does this laptop take? Or are you talking about a completely different laptop altogether?

---

### Post by abridge on 2007-09-27
sry i meant what kind of wireless cards does the laptop use. for example the d link dwl g650 airplus.

---

### Post by Shoadow56 on 2007-09-27
Ok, I still think there is more than one way to answer this question. If you are asking what kind of card this laptop uses, it is an integrated Realtek "card". If you want to find the driver for it I believe it is RTL8185 or something similar to that.

If you are asking what kind of wireless cards this laptop will take in addition to the integrated, then you are looking for a card that looks like this:

[*_Belkin F5D8073 ExpressCard Wireless N Network Adapter_*]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3173667&CatId=2692")

Although I wouldn't reccomend this particular card because I couldn't find any Linux support for it.

I hope that answers your question.

---

### Post by adrianherr on 2007-10-08
Hi chocolatetoothpaste,

I was looking for more details on the fix you have for the MT3705 wifi.
Can you please send me the details?

Thanks

---

### Post by rkrisher on 2007-10-13
Here are the steps to get your wireless and audio working on the MT3705 Debian Etch.  I've done it 5 times now and know it works.  I am using Debian and the KDE desktop.  For some reason I have a hard time with audio in GNOME.  

Fresh install with network connection.  I did everything logged in as root.

Get the Debian module-assistant application with Synaptic Package Manager or "apt-get install module-assistant"

in root console type "module-assistant" to run the app, then select PREPARE.  This will install the kernel and the correct version of compilers to compile the kernel.  Alternatively you can run "module-assistant prep" at the console. 

Install the following packages via Synaptic Package Manager or apt-get:
g77
gpc
kde-extras

Get the "rtl8180-sa2400-dev" from [https://rtl-wifi.svn.sourceforge.net/svnroot/rtl-wifi/](https://rtl-wifi.svn.sourceforge.net/svnroot/rtl-wifi/) and save it somewhere.  I made a drivers directory under root's home and put it there.

In root console in the rtl8180-sa2400-dev directory you created, type the following:

make
sh module_load
dmesg
ifconfig wlan0 up

make the following directory: /lib/modules/2.6.18-5-686/kernel/drivers/net/wireless/rtl8180

copy all .ko files created from the make process in your rtl8180-sa2400-dev directory to the rtl8180 directory you created.  They will be ieee80211_crypt-r8180.ko, ieee80211_crypt_wep-r8180.ko, ieee80211-r8180.ko  and r8180.ko 

in the root console run:

depmod
modprobe r8180
modprobe ieee80211-r8180
modprobe ieee80211_crypt-r8180
modprobe ieee80211_crypt_wep-r8180

In the kde start menu, go to settings/Internet & Network/Network Settings.  Highlight "wlan0" and select "Configure interface..."

Select "Automatic" DHCP and optionally "Activate when computer starts"
NOTE" "Activate when computer starts" will display on boot the wireless adapter trying to search for a DHCP server and connect, if it can.  You can "CTRL-C" past the DHCP discovery process while it is booting up.

I use KWiFiManager to handle my connection to a network.  When I am on the road in motels, some of the network names have spaces in them that other WiFi Manager's can't handle. KWiFiManager works fine for networks with spaces in the names. KWiFiManager is on the kde start menu Internet/More Applications menu.  After launching, make sure to select Settings/Stay in systray on close.  KWiFiManager will then be started everytime you log in and be in your system tray.  

Select "Scan for networks.." to display available wireless networks.  There is a column for encryption in the listed networks.  click on the field under this column next to the network you want to connect to and select "Connect to this network.."  If you are connecting to a WEP encrypted network, then type in the WEP key where it says "on" in the encrypted column.  It takes a while to get a DHCP IP from the network so I speed it up by going to the kde start menu, go to settings/Internet & Network/Network Settings.  Highlight "wlan0" then disable and enable again.  KWiFiManager will then show the IP it got from the wireless network.

You can save your wireless networks in KWifiManager by going to Settings/Configuration Editor...  This is good for WEP because you can add your password here instead of when you scan/connect. Just use the "Activate" button to connect to your network and skip the whole scan / type key / connect process above.  This is the same feature under settings/Internet & Network/Wireless Network.

Now for the audio....do these steps as outlined in a previous reply.  If your skipping directly to this part, make sure you did your module-assistant prep and other compiler installs listed above. Don't go into module-assistant ALSA or the following won't work until you use your package manager to completely remove anything ALSA and install it again. You'll read about it in a later post.

go to:
[ftp://ftp.silug.org/pub/alsa/driver](ftp://ftp.silug.org/pub/alsa/driver)
download:
alsa-driver-1.0.15rc1.tar.bz2

go to:
[ftp://ftp.silug.org/pub/alsa/lib/](ftp://ftp.silug.org/pub/alsa/lib/)
download:
alsa-lib-1.0.15rc1.tar.bz2

go to:
[ftp://ftp.alsa-project.org/pub/utils/](ftp://ftp.alsa-project.org/pub/utils/)
download:
alsa-utils-1.0.15rc1.tar.bz2

go to:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036)
download:
patch_sigmatel.c.patch-1.0.15rc1-simple
15rc1_patch_install

make sure they are all in the same folder and then cd to the folder

edit the 15rc1_patch_install to look like this:

tar xfj alsa-driver-1.0.15rc1.tar.bz2 
tar xfj alsa-lib-1.0.15rc1.tar.bz2 
tar xfj alsa-utils-1.0.15rc1.tar.bz2 
patch alsa-driver-1.0.15rc1/alsa-kernel/pci/hda/patch_sigmatel.c < patch_sigmatel.c.patch-1.0.15rc1-simple
cd alsa-lib-1.0.15rc1/
./configure && make && make install
cd ../alsa-utils-1.0.15rc1/
cd alsaconf/po
cp ../../po/ja.gmo .
touch ru.gmo
cd ../..
./configure && make && make install
cd ../alsa-driver-1.0.15rc1/
./configure && make && make install
alsaconf 
alsactl store

Save the file and run it from your root console in the directory where all your files sit as "sh 15rc1_patch_install" or "./15rc1_patch_install"...whatever suits you.  Reboot and you should hear your sounds when you log into KDE.  To change the startup sound and other sounds, use the KDE "Control Center", select  Sounds & Multimedia/System Notifications.

During boot you will see a message like ......patch_si3054.c:238: si3054: cannot initialize. EXT MID = 0000.  This is your modem.  When I figure it out I'll post it how to get it woking.  I need it for on the road dial-up networking like peoplepc.com.

---

### Post by ngeddes on 2007-10-16
Will this work on Ubuntu?

How do I get into the rootconsul?

Neil

---

### Post by Sharpiedeluxe on 2007-10-19
Okay, so for the MT3705, gutsy seems to support my wireless card :) Unfortunately, I'm still having trouble with the audio. I compiled and installed alsa 1.0.15 , but when I open volume control, it can't find any devices. Unless alsa 1.0.15 didn't include the patch from rc1, then I don't know what the problem is. Someone please help :confused:

---

### Post by rkrisher on 2007-10-21
One other thing that came to mind was that I have the BIOS patch installed from Gateway's website that was supposed to enhance VISTA.  I don't know if that is what might cure some of your problems with audio.  When I first run the patch, it will say "no device found" when it runs the "alsactrl store" line in the patch file, but if I reboot right away it works.  The patch is also dependent on the directory where you put all the file to compile still being around.  If you delete the directory, it won't load the sound drivers.  I'll be back in a few with a fix for that.  Have a feeling I need to do the same thing with the *.ko files I did with the net card.

---

### Post by rkrisher on 2007-10-21
> **ngeddes said:**
> Will this work on Ubuntu?

How do I get into the rootconsul?

Neil

If your logged in as root, just go to "console" off your menu.  You can also run the command "gksu" from the start menu, run command, at least in kde. If your console shows a "$" at the end, your not logged in to the console as root.  log into root by entering "su root".  You'll be prompted for the root password and your prompt should change to a "#".

---

### Post by rkrisher on 2007-10-21
For the sound, do a "lsmod" in console.  You should see this.

[INDENT]snd_hda_intel--------263484--3
snd_pcm_oss----------38496--0
snd_mixer_oss--------15648--1-snd_pcm_oss
snd_pcm---------------69796--3-snd_hda_intel,snd_pcm_oss
snd_timer--------------20836--2-snd_pcm
snd_page_alloc---------9640--2-snd_hda_intel,snd_pcm
snd_hwdep-------------8900--1-snd_hda_intel
snd---------------------51044-10-snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
[/INDENT]
These files should be located in your /lib/modules/2.6.18-5-686/kernel under these directories:
[INDENT]
sound/pci/hda______snd-hda-intel.ko_____346,830_______[date you compiled]
sound/acore/oss____snd-pcm-oss.ko_______44,978
sound/acore/oss____snd-mixer-oss.ko______19,615
sound/acore_______snd-pcm.ko___________83,531
sound/acore_______snd-timer.ko__________26,586
sound/acore_______snd-page-alloc.ko_______12,988
sound/acore_______snd-hwdep.ko_________11,906
[/INDENT]
If they are not there, then the compile didn't go right.  The compile script puts them there.  Troubleshoot your compile.  You can do this by executing every line in the 15rc1 script by hand in the console.  

Check the output of the ./configure and make processes by using a ">" to redirect output to a file. For example "make > output.txt" will put in output.txt everything that would have gone to your console window and scrolled out of reach.  Then edit the text file with vi, kedit or whatever you like.  There are some warnings of things found but not used, they are ok.  Errors are usually obvious. The ./confgure just looks to make sure you have everything needed for the make process. 

Attached to this post are all my ko files above in a zip.  You can just insert them where they need to go and type "depmod -a" in a console so that the kernel knows it needs them.  Then, in the console,  "modprobe" each one of them, without the ".ko" part and underscore instead of dashes,  and make sure you get no error message. i.e "modprobe snd_hda_intel"  Do a "lsmod" to make sure they got inserted by comparing to the above.  Then run your "alsaconf" and "alsacntl store".  Card found should be "hda-intel ATI Technologies Inc SB450 HDA Audio (rev 01)".

Console screen should look like this when it's done.

[INDENT][I]Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-timer snd-page-alloc snd-hwdep.
Building card database...


Running update-modules...
Loading driver...
Setting default volumes...


===============================================================================

 Now ALSA is ready to use.
 For adjustment of volumes, use your favorite mixer.

 Have a lot of fun![/I][/INDENT]

First run may show "device not found" before the "Have a lot of fun!"  but works fine on reboot and subsequent use of "alsaconf".

Don't forget to check out the possibility of the bios patch i mentioned a couple posts ago.

---

### Post by Sharpiedeluxe on 2007-10-21
Okay, thanks for your help, but modprobe wouldn't work..even in root. I ended up downgrading and going back to feisty. Then, everything you stated seemed to work. Thanks for your help. :)

---

### Post by Sharpiedeluxe on 2007-10-21
Okay, I just upgraded back to gutsy. Everything works perfectly now. What I did was, I kept the old library files and I also kept the old feisty kernel. This seems to fix all problems. Nautilus has not frozen thus far, wireless works, audio works. I'll comment back if I experience any trouble. Thanks for the help! :guitar:

---

### Post by Xeroflux on 2007-10-22
I have a gateway mt3705, and i am having the same problem, i just upgraded to ubuntu 7.10, and now i see my wifi, but after i put in the password, my computer freezes, and my sound also still doesn't work, i don't now how to do the bios thing to see if thats my problem or not. And i am completely new to ubuntu.

---

### Post by dboot on 2007-10-22
> **Xeroflux said:**
> I have a gateway mt3705, and i am having the same problem, i just upgraded to ubuntu 7.10, and now i see my wifi, but after i put in the password, my computer freezes, and my sound also still doesn't work, i don't now how to do the bios thing to see if thats my problem or not. And i am completely new to ubuntu.

I'm having the exact same issue with the same model gateway. Any help would be appreciated!

---

### Post by PreviousN on 2007-10-23
Here's how you fix the sound problem. Ive got a Gateway MT3707, so its got the same device. [https://bugtrack.alsa-project.org/alsa-bug/login_page.php?return=%2Falsa-bug%2Fview.php%3Fid%3D3036](https://bugtrack.alsa-project.org/alsa-bug/login_page.php?return=%2Falsa-bug%2Fview.php%3Fid%3D3036)
Click on "guest login without account".READ THE PAGE. I know its tedious, but if you don't read the page but follow the instructions below, you will be boned.  What you need to do is compile from source. 

Here's a script I wrote (kinda)...its attached. Download it, then open a termianl and type "cd /home/(username)/Desktop && sudo chmod +x Sound.Gateway.MT3707" Assuming you downloaded the script to your desktop. 

Now, to use it, log out of GNOME and then press "Ctl+Alt+F1 (or F2-F6)" Log into a shell with your username and password. 

Now run the script: "/home/(username)/Desktop/Sound.Gateway.MT3707" (assuming you downloaded the script to your desktop. 

NOTE BEFORE RUNNING THE SCRIPT:
apt-get remove alsa-base & alsa-utils will uninstall GNOME. This is why I have "apt-get install GDM Ubuntu-Desktop" at the end of this. 

For the record, I take no responsibility if my script bones your system. I've done the best I can to make it work...but I usually don't ever trust anonymous scripts running as root..so take a looksee and make sure that this won't bone your system.

Download these files into /usr/src from the link above:
 patch_sigmatel.c.patch-1.0.15rc1-simple [^] (462 bytes) 09-09-07 22:58
 15rc1_patch_install [^] (449 bytes) 09-09-07 22:59

The contents of the script file:
sudo -i
apt-get install build-essential gettext ja-trans
cd /usr/src
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc1.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc1.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2)
tar xjf alsa-lib-1.0.15rc1.tar.bz2
tar xjf alsa-driver-1.0.15rc1.tar.bz2
tar xjf alsa-utils-1.0.15rc1.tar.bz2
patch alsa-driver-1.0.15rc1/alsa-kernel/pci/hda/patch_sigmatel.c < patch_sigmatel.c.patch-1.0.15rc1-simple
cd alsa-lib-1.0.15rc1/
./configure && sudo make && sudo make install
cd /usr/src/alsa-utils-1.0.15rc1/
./configure && sudo make && sudo make install
cd /usr/src/alsa-driver-1.0.15rc1/
./configure && sudo make && sudo make install
alsaconf
alsactl store
apt-get install gdm ubuntu-desktop


For the record, is there some way that all of us can link together so that if we have problems with similar hardware we can tell others about it?

---

### Post by PreviousN on 2007-10-23
Here's how to fix your wireless:

type "lsmod | grep 8180" find the name of the module. Next type 

"modprobe -r *name of module(s) with 8180*
restart. 

Now, set up wireless using ndiswrapper:

Follow these instructions from [http://ubuntuforums.org/showthread.php?t=555008](http://ubuntuforums.org/showthread.php?t=555008) (searc the page for  Motoxrdude - he attached the driver to his comment)
sudo ndiswrapper -m
sudo ndiswrapper -i net8185.inf
sudo modprobe ndiswrapper

Now all should be fine! Wee!

By the way, since I think all of us with a mt370* should hook up to share infos, is there some way the two things I just wrote could be a sticky for MT370* users? Plus I dont' even care if i get credit. If somoene wants to take my infos and put it in more understandable english then so be it.

---

### Post by ngeddes on 2007-10-23
I think hooking up is a great idea.  Any suggestions?


I got the sound working in Feisty but Flash Player doesn't produce any sound.  Last night I upgraded to Gutsy.  I did it over night.  Servers are very busy.  I fired it up this morning and my wired internet isn't working.

System frooze when I tried to configure.  I rebooted into windows and will try again later and report.

---

### Post by rkrisher on 2007-10-23
> **Xeroflux said:**
> I have a gateway mt3705, and i am having the same problem, i just upgraded to ubuntu 7.10, and now i see my wifi, but after i put in the password, my computer freezes, and my sound also still doesn't work, i don't now how to do the bios thing to see if thats my problem or not. And i am completely new to ubuntu.

Here is the link to the BIOS upgrade:

[http://support.gateway.com/support/drivers/getFile.asp?id=21002&dscr=Windows%20Vista%20BIOS%2083.05&uid=175666718](http://support.gateway.com/support/drivers/getFile.asp?id=21002&dscr=Windows%20Vista%20BIOS%2083.05&uid=175666718)

---

### Post by rkrisher on 2007-10-24
> **Sharpiedeluxe said:**
> Okay, thanks for your help, but modprobe wouldn't work..even in root. I ended up downgrading and going back to feisty. Then, everything you stated seemed to work. Thanks for your help. :)

If you have problems with modprobe, you can use insmod and rmmod instead.  You'd have to be in the directory of the .ko file your trying to insert.  rmmod is for removing a module your trying to update that already may be assigned that you can see with lsmod.  you can "man" the commands for more help.  

THANKS for letting me know it worked!  I'd hate to think I did all the work to post it and it didn't work for anyone!

---

### Post by Xeroflux on 2007-10-24
Hey thanks guys, i haven't had a chance to try fixing it yet, but the help is awesome, and i think that we 370* users should stick together too.

---

### Post by ssx01 on 2007-10-25
I performed a Fresh install of Feisty off my live CD. I then installed the correct video drivers and all the useful codecs off medibuntu, then I upgraded the heck out of it with the upgrade manager, rebooted, and lastly used the upgrade manager again to upgrade to Gutsy, and I have excellent wifi *and* audio with my MT3705.

To be honest, i jumped to the end of this thread, so if somebody has suggested this, flame away. I'm new here- I hope this is helpful to somebody.

---

### Post by rkrisher on 2007-11-01
> **ssx01 said:**
> I performed a Fresh install of Feisty off my live CD. I then installed the correct video drivers and all the useful codecs off medibuntu, then I upgraded the heck out of it with the upgrade manager, rebooted, and lastly used the upgrade manager again to upgrade to Gutsy, and I have excellent wifi *and* audio with my MT3705.

To be honest, i jumped to the end of this thread, so if somebody has suggested this, flame away. I'm new here- I hope this is helpful to somebody.

Does your modem work?

---

### Post by chocolatetoothpaste on 2007-11-03
> **Xeroflux said:**
> Hey thanks guys, i haven't had a chance to try fixing it yet, but the help is awesome, and i think that we 370* users should stick together too.

Someone could just start a page in the wiki or the community docs, and contain a lot of the information from this thread.  I've seen the same thing done for other laptop models.

---

### Post by ngeddes on 2007-11-04
I upgraded my MX3701 to Gutsy last Sunday and lost both sound and wi-fi.  The sound problem I fixed by running the ALSA patch that worked on Feisty but still Adobe Flash Player won't run.

Worse the wireless is completely broken.  If I boot up with my card active, Gutsy crashes.  If I turn on the card or even try and unclick the wireless option in the Network menu, she crashes.

---

### Post by chocolatetoothpaste on 2007-11-09
Has anyone been able to get their sound to work using the 1.15 stable release of alsa?  I tried to compile/install it by itself, then making a couple changes to the patch script discussed earlier in this thread.  Just wondering if anyone can help out.  I have had the rc1 release working before, but would prefer to use a stable release.  TIA

---

### Post by JasonJG on 2007-11-10
Hello I am a newbie when it comes to Linux and Ubuntu overall, but I think i have figured this sound thing out.  here are the steps i took and Have sound working on Three different models of these laptops.  ML3109 Celeron M520, MT3708 Pentium Dual Core, and finally This an MX3422 AMD X2.  

I searched for the ALSA files in Synaptic Package Manager and removed the ALSA Base.
Then I download all three dont know if i really needed them.  ALSA packages from Alsa Project.  I used the newest release.  I ran the regula ./configure, then make, then make install on all three packages, Driver, Lib, and Utils.  I am pretty sure the Utils didnt completely finish.  Soon as I rebooted I have sound!!!!!  If i can help please let me know but I think this should fix everyones problems with out the patch that is out there, I couldnt seem to get it to work.

As for the Wireless I blacklisted r8180, r818x, and rtl8187  and installed ndiswrapper and download the realtek wireless driver for XP from realteks website and then added ndiswrapper to the /etc/modules at the end of the line.  Laptop boots with Sound & Wireless.

---

### Post by chocolatetoothpaste on 2007-11-11
Thanks for the tip, JasonJG.  I was able to get my sound working by uninstalling any alsa packages that were installed, then I did the same as you and compiled the 3 packages form source and it worked!  I installed a command-line only install and I compiled openbox from source.  After which, I installed a few other programs, and needless to say I am very happy with my super slim OS.  It runs wicked fast!

Edit: Okay, I have another issue now.  When I restart my computer, the sound is muted by default.  Does anyone know how to fix this?

---

### Post by Speedstix on 2007-11-15
I can happily say that I have fixed both audio and wifi on my gateway mt3705.
I fixed wifi by swapping for a linux compatible wireless card and I fixed speakers by following the link below. Before going to the link make sure that you have the "build-essential" package installed from Synaptic. Amazing

The link is here:
[http://donnieknows.com/bin/view/Main/GatewayML3109](http://donnieknows.com/bin/view/Main/GatewayML3109)

EDIT: I forgot to mention that this setup currently works on Ubuntu 7.04, I also had to rerun the script to return sound after a major update.

---

### Post by lvleph on 2007-12-02
> **JasonJG said:**
> Hello I am a newbie when it comes to Linux and Ubuntu overall, but I think i have figured this sound thing out.  here are the steps i took and Have sound working on Three different models of these laptops.  ML3109 Celeron M520, MT3708 Pentium Dual Core, and finally This an MX3422 AMD X2.  

I searched for the ALSA files in Synaptic Package Manager and removed the ALSA Base.
Then I download all three dont know if i really needed them.  ALSA packages from Alsa Project.  I used the newest release.  I ran the regula ./configure, then make, then make install on all three packages, Driver, Lib, and Utils.  I am pretty sure the Utils didnt completely finish.  Soon as I rebooted I have sound!!!!!  If i can help please let me know but I think this should fix everyones problems with out the patch that is out there, I couldnt seem to get it to work.

As for the Wireless I blacklisted r8180, r818x, and rtl8187  and installed ndiswrapper and download the realtek wireless driver for XP from realteks website and then added ndiswrapper to the /etc/modules at the end of the line.  Laptop boots with Sound & Wireless.

You can use the [donnieknows enable_sound.sh](http://donnieknows.com/pub/Main/GatewayML3109/enable_sound.sh) to do this. In his script he uses the rc1, but this is easy to change. All you need to do is edit his script and remove all the rc1 references. Then comment out anything to do with his patch. Now you have a script that does it all for you. I am testing this method out right now to see if it works for me.

EDIT: This did not work for me for either kernel (2.6.22-14 or 2.6.20-16). I added the patch back in, and reinstalled alsa-base. Then ran the script. Still had no sound in either kernel. However, in 2.6.20-16 I noticed that it recognized I had a card, and that I could push mute unmute, but alsa stayed in mute. Opened a terminal and type alsamixer. There it was, the main volume was muted. Turned that up all the way, and voi la I had sound, but only in 2.6.20-16. The newer kernel says no-such device. Not sure the issue there.

---

### Post by lvleph on 2007-12-04
Has anyone been able to get sound on gutsy?

I will provide the specific error I get once I am home.

EDIT: I missed two important post. I will try those solutions when I get home.

---

### Post by ProBo on 2007-12-18
I have tryed the solution at the top of the page and it didn't work. I really want sound, and I really don't want to switch back to Vista...

BTW im really new at this, and i really like it so far.... except for this issue, but i have alreay found more support than i have had for Vista!

---

### Post by lvleph on 2007-12-18
> **ProBo said:**
> I have tryed the solution at the top of the page and it didn't work. I really want sound, and I really don't want to switch back to Vista...

BTW im really new at this, and i really like it so far.... except for this issue, but i have alreay found more support than i have had for Vista!

If you don't mind compiling a kernel, you can try [this](http://ubuntuforums.org/showpost.php?p=3887733&postcount=86). I am currently trying to figure it out with out compiling a kernel. Also, you could just use 7.04 instead, and the donnieknows method will work. I am almost about to resort back to that.

---

### Post by ProBo on 2007-12-18
> **lvleph said:**
> If you don't mind compiling a kernel, you can try [this](http://ubuntuforums.org/showpost.php?p=3887733&postcount=86). I am currently trying to figure it out with out compiling a kernel. Also, you could just use 7.04 instead, and the donnieknows method will work. I am almost about to resort back to that.

unfortunatly i need sound today, so i may have to go back to vista till a definite solution is found...

---

### Post by lvleph on 2007-12-18
Well, Ubuntu 7.04 and [donnieknows](http://donnieknows.com/bin/view/Main/GatewayML3109) will get you sound today. If that is all you want, and don't care which version of Ubuntu you use.

---

### Post by lvleph on 2007-12-18
Okay, ignore the last post. I have sound working in Gutsy!

Here is what you need to do.
Open software sources
System>>administration>>software sources>>updates tab>>click Unsupport Updates>>close
Open synaptic package manager
System>>administration>>synaptic package manager
search for backports and then select linux-backports-modules-2.6.2 2.6.22-14.11
Now click apply
Once that is done restart your system.
Sound!

---

### Post by ProBo on 2007-12-27
has anyone else tested the last post? im running vista again and if it works im switching back

---

### Post by lvleph on 2007-12-27
> **ProBo said:**
> has anyone else tested the last post? im running vista again and if it works im switching back

It is still working for me. The backports package name may have changed by now, because of updates. You can check my other posts on the subject and you will see others that say it works.

---

### Post by Speedstix on 2007-12-28
I can see a few of you are having troubles with sound on this gateway mt3705. I provided information that I found to be very helpful because I got sound on ubuntu 7.04. I first had ubuntu 7.10 installed and found it to run very slowly on my laptop, the initial loading screen was just all black with nothing showing loading progress. 
I was wondering if anyone else had that problem with 7.10?

I am also not sure if sound works using the method I mentioned above (top of page).
From what I am reading people are getting mixed results with this elusive sound problem.

---

### Post by lvleph on 2007-12-28
The usplash screen does not have the corrct resolution. You need to change that.

```
sudo gedit /etc/usplash.conf
```

Change the resolution to 1280x800 (or whatever your resolution is set to). It is probably set to 1280x1024.

For anyone having trouble with their gaphics card and 3d acceleration, use [Envy](http://albertomilone.com/nvidia_scripts1.html) to get it to work. I am not sure which ati driver that program installs, and so there may still be an issue with suspend and hibernation. I just got the graphics working yesterday, so I have not had a whole lot of time to test it. I can confirm that 3d acceleration does work using Envy. I am now running compiz.

---

### Post by rkrisher on 2008-01-28
For those of you trying to upgrade to Debian Lenny, here is how I got my wifi working.

other drivers won't compile that I posted previously for Debian Etch.

download patch from:

[http://sourceforge.net/tracker/download.php?group_id=114161&atid=667396&file_id=243347&aid=1783995](http://sourceforge.net/tracker/download.php?group_id=114161&atid=667396&file_id=243347&aid=1783995)

open terminal(root)
cd into directory
make
md /lib/modules/2.6.22-3-686/kernel/drivers/net/wireless/rtl8180
cp *.ko /lib/modules/2.6.22-3-686/kernel/drivers/net/wireless/rtl8180
depmod
modprobe r8180
modprobe ieee80211-rtl
modprobe ieee80211_crypt_wep-rtl
modprobe ieee80211_crypt_tkip-rtl
modprobe ieee80211_crypt_ccmp-rtl
enable (in kde its kmenu/settings/network)

This  patch doesn't seem to report signal strength but everything else seems to work plus it has tkip and ccmp.

Now I'm gonna try getting the sound to work with the new kernel.

---

### Post by ctlongley on 2008-02-28
Not sure if you still have the audio problems, but I created a thread for the numerous people having the same problem. This fixed my sound card on a 3707, and could also work for a 3705. Hope it works for you as well.

[http://ubuntuforums.org/showthread.php?t=710343](http://ubuntuforums.org/showthread.php?t=710343)

---

### Post by ack88 on 2008-03-06
The solution to the sound problem for the MT3705 is here:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I was able to get the sound working with that tutorial and the following alsa files:

alsa-driver-1.0.16rc2
alsa-lib-1.0.16rc2
alsa-utils-1.0.16rc1

Good luck everyone.

---

### Post by lvleph on 2008-03-06
I just use the backports and the soud works.

---

