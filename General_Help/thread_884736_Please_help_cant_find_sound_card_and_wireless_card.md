---
title: "Please help cant find sound card and wireless card drivers"
date: 2008-08-09
forum: General Help
---

### Post by wertyer on 2008-08-09
I just installed ubuntu(dual boot windows) yesterday and when I first booted it up I realized that the sound and internet didn't work.  I realized that I must need to find the drivers for them, but I couldn't find find them.  My sound card is a Creative SB Audigy and my wireless internet card is 		
1394 Net Adapter
IEEE 802.11b Wireless Cardbus/PCI Adapter.  If someone could help me find the drivers for these it would be GREATLY appreciated!

---

### Post by pytheas22 on 2008-08-09
I don't know much about sound, but I will try to help with the wireless if you post the output of:
```

lspci -nn
lshw -C Network
```

---

### Post by dexter on 2008-08-09
The soundcard should work out of the box. I'm using it and Ubuntu has always been able to use it.

What version are you running? Do you used a selfcompiled kernel?

Show us the output of 
```

lspci | grep audio
lsmod | grep emu

```

---

### Post by wertyer on 2008-08-09
I am running Ubuntu 8.04 LTS.  And I know this is a very noob question but where exactly do I need to type that stuff?  Thanks for the help!

---

### Post by pytheas22 on 2008-08-10
> I am running Ubuntu 8.04 LTS. And I know this is a very noob question but where exactly do I need to type that stuff? Thanks for the help!

Don't worry, we were all foreigners to the command-line at some point :)

You can launch a terminal from Applications>Accessories>Terminal; once there, enter those commands, one per line, and press enter after each command to get its output.

To copy-and paste-terminal output, first highlight the text you want to copy with your mouse, then right-click and select 'copy.'  Then paste the text (with control-v) here.  [If you don't have any Internet connection on Ubuntu and therefore can't post in these forums from there, open up a text file (Applications>Accessories>Text Editor) and paste the information there.  Then save the file and transfer it to a computer that has Internet via a USB stick or whatever you have handy so that you can copy-and-paste from there.]

---

### Post by wertyer on 2008-08-10
Ok here is the output for the sound card:

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
cody@cody-desktop:~$ 
cody@cody-desktop:~$ lsmod | grep emu
snd_emu10k1_synth       8064  0 
snd_emux_synth         36224  1 snd_emu10k1_synth
snd_seq_virmidi         8192  1 snd_emux_synth
snd_seq_midi_emul       7552  1 snd_emux_synth
snd_emu10k1           146880  4 snd_emu10k1_synth
snd_ac97_codec        101028  2 snd_intel8x0,snd_emu10k1
snd_pcm                78596  4 snd_intel8x0,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_util_mem            5632  2 snd_emux_synth,snd_emu10k1
snd_rawmidi            25760  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_hwdep              10500  2 snd_emux_synth,snd_emu10k1
snd_seq                54224  9 snd_emux_synth,snd_seq_dummy,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9612  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_emu10k1,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  25 snd_emux_synth,snd_intel8x0,snd_seq_dummy,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11400  3 snd_intel8x0,snd_emu10k1,snd_pcm


and this is for the wireless card:


  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
  *-network:1 DISABLED
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 82
       serial: 00:07:e9:89:56:63
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes


 And thanks pytheas22 for the idea of copying and pasting into a txt file cuz that made things muck easier.

---

### Post by pytheas22 on 2008-08-10
Thanks for the information.  Your card may be a little difficult to get working, but it should be possible.  To figure out the best route to take, though, I need to ask for a little more information.  Please post the output of:
```

lspci -nn
lsusb
```

And please also tell me whether you need to connect to a WEP or WPA-encrypted network or not (as some drivers may not work with encryption).

---

### Post by jocko on 2008-08-10
The drivers for your sound card are loaded and in use, so you should have sound.
I also see from your lsmod that you have the snd-intel8x0 module loaded. I guess that's because you also have an onboard ac'97 sound chip?

One thing you can try is to configure alsa to use your audigy as default card.
Copy this command and paste it into a terminal:```

asoundconf list
```
That will give you the name(s) of your sound card(s).
Next type this command into the terminal:
```
asoundconf set-default-card [COLOR=Blue]your_card[/COLOR]
```Where [COLOR=Blue]your_card[/COLOR] is the name of the card you want to have as default, written **exactly** as in the output of the first command.
To use the new configuration, you may need to log out and log in again.

Type "alsamixer" in the terminal. Here you can set the volumes for every channel your sound card has. Use the arrow keys to switch between different channels and change their volumes. If there is a box containing "MM" below a slider it is muted, press M once to unmute it (you should now see "00" instead). Press Esc to quit alsamixer.

Next, you probably want to be able to play more than one sound at once, which can be done by setting alsa to use pulseaudio as a software mixer, with this command:```
asoundconf set-pulseaudio

```Again, you may need to log out and in again to see if this had any effect.

---

### Post by wertyer on 2008-08-10
> **pytheas22 said:**
> Thanks for the information.  Your card may be a little difficult to get working, but it should be possible.  To figure out the best route to take, though, I need to ask for a little more information.  Please post the output of:
```

lspci -nn
lsusb
```

And please also tell me whether you need to connect to a WEP or WPA-encrypted network or not (as some drivers may not work with encryption).


Ok here is the output:

00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC [10ec:8180] (rev 20)
01:01.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 03)
01:01.2 FireWire (IEEE 1394) [0c00]: Creative Labs SB Audigy FireWire Port [1102:4001] (rev 01)
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller [8086:1039] (rev 82)
cody@cody-desktop:~$ 
cody@cody-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 001 Device 001: ID 0000:0000  


and also there is no encryption on the internet connection that I connect to.


And also about the soundcard I tired everything you told me but i didn't work.  All I can hear is beeps.  Is there a way to disable my motherboard soundcard?  Maybe that would work.

---

### Post by jocko on 2008-08-10
> **wertyer said:**
> And also about the soundcard I tired everything you told me but i didn't work.  All I can hear is beeps.  Is there a way to disable my motherboard soundcard?  Maybe that would work.

To disable the onboard soundcard, either enter your computers bios and look for a setting where you can disable it, or try this:
```
gksudo gedit /etc/modprobe.d/blacklist
```Add this line to the file that is opened:
```
blacklist snd_intel8x0
``` That will prevent the driver for the onboard card from being loaded, which should prevent it from becoming the primary sound card (if that's your problem). Reboot to see if it works.

When you say you hear beeps, exactly what do you mean? When do you hear beeps?

---

### Post by pytheas22 on 2008-08-10
Thanks for that extra information about the network card.  I think the best way to go is with ndiswrapper, which lets you drive your card using Windows drivers.  There are also native Linux drivers for your card (which has a Realtek chipset), but they may or may not work so well (I can't find much information about them) and would be harder to install.

To get ndiswrapper going, first put your Ubuntu live CD in your drive (if you don't have an Ubuntu CD, let me know and we can work around it).  Then go to System>Administration>Software Sources and click on the "Ubuntu Software" tab.  Under the "Installable from CD-ROM/DVD" section, check the box to use your CD as a repository.  Then close the window.  You will probably be asked at this point if you want to reload the sources list; say yes.

Next, open up a terminal and run these commands to install ndiswrapper:
```

sudo apt-get install ndiswrapper* ndisgtk
```

You also need to grab Windows drivers for your card.  On a machine that has Internet, click [here]("ftp://ftp.targetgroup.it/digicom/comuni/driver/PalladioWaveC/PalWavC__WIN.zip") to download them.  Then transfer that .zip file to your Ubuntu computer and save it to the desktop there.

Finally, run these commands to install the Windows driver into ndiswrapper:
```

cd ~/Desktop
unzip PalWav*
sudo ndiswrapper -i NETR8180.INF
```

Now reboot, and in principle your wireless card should work.  If it doesn't, please post the output of these commands:
```

lsmod | grep ndis
ndiswrapper -l
uname -m
dmesg | grep -e ndis -e wlan
iwlist scan
```

---

### Post by CKyle22 on 2008-08-10
Try playing an MP3, it should seach for codecs. Download them, and enjoy the sound. I haven't read the thread yet, so if that's been suggested, I'm sorry. But it worked for me. :)

---

### Post by Yellow Pasque on 2008-08-10
I have this chipset and had to use the Windows drivers. Here's how I did it:
Download the driver from Realtek [ftp://210.51.181.211/cn/wlan/ndis5x-8180(173).zip](ftp://210.51.181.211/cn/wlan/ndis5x-8180(173).zip) to your /home folder. Launch the terminal (Applications -> Accessories -> Terminal)
```
unzip ndis5x-8180(173).zip
sudo ndiswrapper -i NET8180.inf
sudo depmod -a
sudo ndiswrapper -m
sudo echo ndiswrapper >> /etc/modules
```
Restart the PC.

---

### Post by wertyer on 2008-08-10
Ok so now all i need to do is install ndiswrapper.  I have a live cd, but it does not give any of those kinds of options.  I think I might have a different live cd.  If someone can tell me where to download ndiswrapper and how to get it working I think I should be ok.

---

### Post by Yellow Pasque on 2008-08-10
ndiswrapper should be on the livecd. Do a search in nautilus.

---

### Post by pytheas22 on 2008-08-10
> Ok so now all i need to do is install ndiswrapper. I have a live cd, but it does not give any of those kinds of options. I think I might have a different live cd. If someone can tell me where to download ndiswrapper and how to get it working I think I should be ok.

Yes, the ndiswrapper packages come on the Ubuntu CD.  You can find them there manually, as the poster above suggests.  Or you can enable the CD to be used as a repository, as I outlined in my last post, and after that, you should be able to install them with the command:
```

sudo apt-get install ndiswrapper*
```

A third option is to download the packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/).  ndiswrapper requires two packages: [ndiswrapper-common]("http://packages.ubuntu.com/hardy/ndiswrapper-common") and [ndiswrapper-utils-1.9]("http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9").  Once you download the .deb packages, transfer them to your Ubuntu machine and double-click each one to install.  If the installer complains about missing dependencies, try installing the other package first (they need to be installed in an order but I don't know which one has to be first).

---

### Post by wertyer on 2008-08-11
Ok I installed the wireless card driver, but it didnt work and here is the output of that other stuff:  lsmod | grep ndis
ndiswrapper -l
uname -m
dmesg | grep -e ndis -e wlan
iwlist scan





















cody@cody-desktop:~$ lsmod | grep ndis
cody@cody-desktop:~$ 
cody@cody-desktop:~$ ndiswrapper -l
netr8180 : driver installed
	device (10EC:8180) present
cody@cody-desktop:~$ 
cody@cody-desktop:~$ uname -m
i686
cody@cody-desktop:~$ 
cody@cody-desktop:~$ dmesg | grep -e ndis -e wlan
cody@cody-desktop:~$ 
cody@cody-desktop:~$ iwlist scan


And also I tried to install the sound card driver, but I got an error saying that it was decryted and it wouldn/'t let me install it.

---

### Post by pytheas22 on 2008-08-11
ndiswrapper appears to be installed alright; it just looks like the module isn't being inserted at boot like it's supposed to.  That's easy enough to fix, though.  Please run this command:

```
echo 'ndiswrapper' | sudo tee -a /etc/modules

```

Then reboot and the wireless should be working.  If it still doesn't work at that point, run:
```

sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

and then it should work.  If it still doesn't, please post the output of:
```

lsmod | grep ndis
dmesg | grep ndis
lshw -C Network
iwlist scan
```

so that we can figure out what's going on.

---

### Post by wertyer on 2008-08-11
> **pytheas22 said:**
> ndiswrapper appears to be installed alright; it just looks like the module isn't being inserted at boot like it's supposed to.  That's easy enough to fix, though.  Please run this command:

```
echo 'ndiswrapper' | sudo tee -a /etc/modules

```

Then reboot and the wireless should be working.  If it still doesn't work at that point, run:
```

sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

and then it should work.  If it still doesn't, please post the output of:
```

lsmod | grep ndis
dmesg | grep ndis
lshw -C Network
iwlist scan
```

so that we can figure out what's going on.



Ok I got the card working :) but I can't connect to my internet.  I can see my some other internet connections, but they all use WEPs.  On my internet it is set up so only certain mac addresses can connect.  The internet is set up to use my computer's mac address, but I have a feeling this is the problem.  Does ubuntu change the mac address or do something that would make it not work?

---

### Post by jocko on 2008-08-11
> **wertyer said:**
> The internet is set up to use my computer's mac address, but I have a feeling this is the problem.  Does ubuntu change the mac address or do something that would make it not work?
You should see the mac addresses in the output of the command "ifconfig".

---

### Post by pytheas22 on 2008-08-11
> Ok I got the card working but I can't connect to my internet. I can see my some other internet connections, but they all use WEPs. On my internet it is set up so only certain mac addresses can connect. The internet is set up to use my computer's mac address, but I have a feeling this is the problem. Does ubuntu change the mac address or do something that would make it not work?

It's a good sign that you can see networks now at least.  Ubuntu shouldn't be changing your MAC address, but as the poster above says, you can check what the MAC is by running "ifconfig" and looking at the "HWaddr" entry for "wlan0."  For example, here's mine:

```
wlan0      Link encap:Ethernet  **HWaddr 00:19:e0:67:8a:f1**  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:e0ff:fe67:8af1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:901 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:882205 (861.5 KB)  TX bytes:148579 (145.0 KB)
```


If you still can't connect, please post the output of:
```

iwconfig
iwlist scan
```

and we can give you instructions for connecting from the command-line, which will help troubleshoot whatever's going on (please tell us the name of your network so we know which is which).

One possible thing that you may want to check on is the mode in which your router is operating.  I noticed from your outputs above that your card appears to only support 11b mode, but most networks now operate on 11g.  Are you sure your network is compatible with 11b mode (I know it probably is since I assume you're using the same card to connect in Windows, but I just wanted to check)?

---

### Post by wertyer on 2008-08-11
Ok its not the mac address and I dual boot windows and the card works fine on windows.  And heres the output:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:D7:D0:81
                    ESSID:"homeschool"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:17:3F:EF:B5:CE
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


My connection name is Austin, which I can see is not on that list.  So im guessing thats the problem.

---

### Post by pytheas22 on 2008-08-11
First of all, the belkin54g network doesn't seem to use encryption...can you connect to it, just to test that the card works for that (and to make pasting things here easier)?

I also notice that the two networks that you do see (do you see more networks than that in Windows?) are in 11b mode, which is rare these days.  Please post the output of:
```

iwconfig
```

so that we'll know which mode your card is operating in.

You could also try:
```

sudo iwpriv wlan0 mode 11g
```

and see if that makes a difference--it should force your card to operate in 11g mode, since it seems to be only on 11b now.

A third option is to go to your router's configuration page (usually you get to it by entering "192.168.1.1" or "192.168.0.1" into your web browser on a machine that's connected to your router) and set it to operate only in 11b mode.  Your wireless card should be able to see it then and connect.

Let me know if any of the above helps.

---

### Post by wertyer on 2008-08-12
Ok I can connect to belkin54g, but when it gets fully connected my computer crashes.  I tried connecting to the same network on windows and it worked ok, but not with ubuntu.  What would cause it to crash?

---

### Post by pytheas22 on 2008-08-12
> Ok I can connect to belkin54g, but when it gets fully connected my computer crashes. I tried connecting to the same network on windows and it worked ok, but not with ubuntu. What would cause it to crash

That's strange.  How does it crash exactly--does the whole system lock up completely?  Can you move the mouse?  If you press control-alt-backspace, do you return to the login screen?  You might want to take a look at the system logs (go to System>Administration>System Log) and see what was being logged at the time of the crash.

If there are instability issues with ndiswrapper, there are other ways to get your card working, but I've never seen ndiswrapper cause the whole machine to crash before.  I'm sorry this is so complicated...I thought we were close to a final solution.

---

### Post by Yellow Pasque on 2008-08-12
You're not running 64-bit Ubuntu by chance, are you? I saw you had an ICH4 and assumed you had a 32-bit CPU, but I guess you could have upgraded it.

The 64-bit driver works fine for me on a D-Link DWL 520 rev. D

I don't if the 32-bit driver works properly on Linux or not. YOu might want to do some Googling.

---

