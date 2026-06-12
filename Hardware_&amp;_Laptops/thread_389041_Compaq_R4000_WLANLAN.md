---
title: "Compaq R4000 WLAN/LAN"
date: 2007-03-20
forum: Hardware &amp; Laptops
---

### Post by Greyhaven7 on 2007-03-20
Hello Everyone,
Here's the story:
I've had the Vista beta running on my system for several months now, and it's finally pissed me off to no end. While I used to love Windows, Vista has shown me that Microsoft has no earthly clue how to build a stable operating system. SO, I'm taking my laptop, formatting it, and dual booting into Ubuntu 6.1 and Win2KPro. 

The Ubuntu install went flawlessly. I'm now in the system and all seems well. However, I don't have access to the internet. Here's the rundown:

OS: Ubuntu 6.1 (AMD 64 version) -  Downloaded last night from the front page of Ubuntu's site. Correct me if I'm wrong but this is a 64bit version of Ubuntu, right?

Comp: Compaq Persario R4000 (laptop)

WLAN card: onboard Broadcom BCM4306

LAN card: onboard Realtek RTL-8139 (/....C and /....C+)

Situation: Computer SEES both of the cards and can identify them. It just can't seem to USE them. I haven't been able to find anything on the Realtek card, and my focus was primarily on the WLAN since I'd much rather have that one working. 

Since Broadcom apparently sucks and didn't release drivers for Linux, I'm trying to run them through ndiswrapper. So I've run through the steps, putting ndiswrapper on my desktop, typing in the sudo commands, etc... everything seems to be going well untill... I get an error that says:

> WE HAVE DETECTED THAT YOU ARE USING EDGY EFT WITH AN
********
*INCOMPATIBLE* *64BIT* *KERNEL*
********
Please read: 
http://<<there's a link here but I can't access it since I don't have the internet>>
This is a bug, and a bug report has already been filed. 
Aborting...please rerun after the problem is fixed. 

So, I'm assuming that means that the win kernel it's trying to run in ndiswrapper isn't 64bit and therefore is not working within the 64bit version of Ubuntu, correct? 

So, what do I do to get to the interent? I keep coming up short on solutions for the BCM4306 including one forum post that said:
> If it's a BCM4306, good luck! A lot of banging your head into walls...
I'm new to linux and I don't want to get disheartened, someone please help. 
If you need more info on my system, etc... please let me know.

---

### Post by teaker1s on 2007-03-20
as I understand it the realtek driver is avaliable but not loaded into kernel. to resolve this
```
sudo apt-get install module-assistant
```
```
sudo module-assistant
``` update,prepare,select and install with gui

I'm not sure the module may need modprobe to start and then adding to module loading file-so it loads from boot.

I thought the 4306 was natively supported- lets check in terminal and post output
```
iwconfig
```
I hope this at least gets you started
regards Daniel

---

### Post by Greyhaven7 on 2007-03-20
Ok, I entered those commands in that order into the terminal from:
username@unsername:~$

it asks for the password (obviously) and then says:
> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package module-assist

Then it sends me back to the prompt...

Is it looking on the HDD or is it trying to look on the interent? If it's trying to find something on the interenet it won't have any luck as I have no linux machine capable of reacing the interent to get the package "module-assist"... if that's what's going on. 

I'm at work right now on a WinXP machine, but I have my Ubuntu laptop with me. Is there any way I could find this package with windows and then install it in Ubuntu?

Also, I really need the wireless card working. Having the ethernet card working would be great, but I use a wireless lan at home, so... 

I do really apprecaite your help on either issue. Thank you so much for responding so quickly by the way.

---

### Post by Greyhaven7 on 2007-03-20
Ok, after your edit:
I typed "iwconfig" into the terminal, this is what I got:
> 
lo         
no wireless extensions.

eth0     
no wireless extensions.

eth1     
IEEE 802.11b/g ESSID:"" Nickname:"Broadcom 4306"
           Mode:Managed Access Point: Invalid
           RTS thr: off Fragment thr: off
           Link Quality: 0 Signal level: 0 Noise level: 0
           Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
           Tx excessive retires:0 Invalid misc:0 Missed beacon:0

sit0      
no wireless extensions. 

Thanks for the help. :)

---

### Post by teaker1s on 2007-03-20
my mistake I thought that your sources would have the install cd as one of them, try this
```
sudo apt-cdrom add
``` insert your install cd and re run previous commands

---

### Post by Greyhaven7 on 2007-03-20
Ok, that did a lot of stuff and I can't possibly type it all into this machine to send to you, but here's the synopsis:

It unmounted the cd-rom, then mounted it again
identified it
scanned it for index files
found 2 package indexes, 0 source indexes, 0 translation indexes, and 1 signature

it knows the disc is named "Ubuntu 6.10 _Edgy_Eft_ - Release amd64 (20061025)"

it then coppied package lists... gpgv: Signature... blah blah blahy
it accpeted the signature from the CD

it read the package indexes
it wrote new source list
it says the new source entries from the disc are:
deb cdrom:[Ubuntu 6.10 _Edgy_Eft_ - Rlease amd64 (20061025)/ edgy main restricted

it then unmounted the CD-ROM and said to repeat this process for the rest of the CDs in the set (but there aren't any that I know of, just this one).

---

### Post by Greyhaven7 on 2007-03-20
ok, after running the previous commands:

> sudo apt-cdrom add
That did a bunch of stuff (see previous post)

Then I entered:
> sudo apt-get install module-assistant
and still got the same message as before:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package module-assistant

Did I do something wrong?

---

### Post by dannyboy79 on 2007-03-20
it's saying that the module-assistant package isn't on the cd. can you download module-assistant from Ubuntu Edgy website (.targz file) from another machine, put it on a cd, a floppy, a usb stick, and then put it on your laptop and then uncompress and run the script? i am actually going thru the same thing. I am trying out puppy linux on my ancient laptop and they don't have the ath_pci driver (atheros ar5212 chip) in their iso. Their iso was only 80mb. SO I have to download madwifi_ng source and compile it myself in puppy. luckily I have a winbloz box sitting around connected to the internet.

---

### Post by Greyhaven7 on 2007-03-20
I can't find a downloads section of their site, do you happen to have a link to where I can get the file? Or at least the section of the site that might have downloads on it?

---

### Post by Greyhaven7 on 2007-03-20
Ok, I've found two files called:

module-assistant_0.10.6_all.deb
and
module-assistant_0.10.6.tar.gz

I've put them on my desktop... 

Which is it and how do I install/run it?

Thanks for the help, once I get the internet working, I'm confident the rest of this is going to be easy, I know I just have a SOB of a harware configuration.

---

### Post by teaker1s on 2007-03-20
provided it's a ubuntu deb click the deb file to install

---

### Post by Greyhaven7 on 2007-03-20
lol!
After all the code typing and searching for command meanings, I didn't even try clicking the actual file. 

OK, now it's installed, I typed:
> sudo module-assistant
in the terminal and now I've got a blue and grey window that looks like a BIOS setup screen. 

It says:
> Welcome to the dialog frontend of module-assistant. This user interface provides access to the few commands of this program. 

If you wish to learn more, choose the OVERVIEW optioon.

You should better run UPDATE once before you proceed. If you wish to look for existing module packages for your needs or wish

OVERVIEW
UPDATE
PREPARE
SELECT
EXIT

<Ok>  <Cancel>

I selected Prepare...
it did a bunch of stuff, suggesting packages and telling me what packages were going to be installed...
I selected yes.
It said it was done and went back to menu in the Quote above...
Then I selected "Select"

I'm now looking at a very big list of modules... 
Which one am I looking for?

---

### Post by teaker1s on 2007-03-20
okay back on my ubuntu machine, there appears to not be a separately installable module, please look at this
[http://www.ubuntuforums.org/showthread.php?t=382555&highlight=8139]("http://www.ubuntuforums.org/showthread.php?t=382555&highlight=8139")

it appears the kernel supports this hardware with a module, there are a couple of people with problems- but I think your best bet is above link

---

