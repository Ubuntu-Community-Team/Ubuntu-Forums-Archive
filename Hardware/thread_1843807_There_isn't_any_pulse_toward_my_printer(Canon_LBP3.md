---
title: "There isn't any pulse toward my printer(Canon LBP3100B) ???"
date: 2011-09-14
forum: Hardware
---

### Post by SidebySide on 2011-09-14
_Summary: Ubuntu don't send any message to the printer?_

My Printer Model: [COLOR=DarkOrange]**Canon**[/COLOR] - LBP3100B
I downloaded a "CAPT" driver from Canon official Websit and installed it. Also I followed 2 below commands which is argued [here]("https://help.ubuntu.com/community/CanonCaptDrv190?action=fullsearch&context=180&value=linkto%3A%22CanonCaptDrv190%22").
> The Canon CAPT printer driver is split into two packages: cndrvcups-capt  and cndrvcups-common  available from the Canon printer driver PPA. As  of April 2011, this PPA contains 2.20 version of the Canon drivers,  build for i386 and amd64 on both Lucid and Maverick. This is the easiest  way to install the drivers.
To add the PPA to your system and install the packages do:[SIZE=1][COLOR=DarkRed]
sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get install cndrvcups-capt cndrvcups-common[/COLOR][/SIZE]
```
sudo add-apt-repository ppa:michael-gruz/canon
```[SIZE=2][COLOR=DarkGreen]OUTPUT:[/COLOR][/SIZE]
[SIZE=1]Executing:  gpg --ignore-time-conflict --no-options --no-default-keyring  --secret-keyring /etc/apt/secring.gpg --trustdb-name  /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring  /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv  84E550CD36EC35430A66AC5A03396E1C3F7B4A1D
gpg: requesting key 3F7B4A1D from hkp server keyserver.ubuntu.com
gpg: key 3F7B4A1D: "Launchpad Misakovi" not changed
gpg: Total number processed: 1
gpg:  unchanged: 1[/SIZE]

```
sudo apt-get install cndrvcups-capt cndrvcups-common
```[SIZE=1][SIZE=2][COLOR=DarkGreen]OUTPUT:[/COLOR][/SIZE]
[/SIZE][SIZE=1]Reading package lists... Done
Building dependency tree        
Reading state information... Done
cndrvcups-capt is already the newest version.
cndrvcups-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 718 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up alsa-driver-linuxant (1.0.16.1-1) ...
ln: creating symbolic link `/etc/rc0.d/K92alsasound': File exists
ln: creating symbolic link `/etc/rc1.d/K92alsasound': File exists
ln: creating symbolic link `/etc/rc2.d/S08alsasound': File exists
ln: creating symbolic link `/etc/rc3.d/S08alsasound': File exists
ln: creating symbolic link `/etc/rc4.d/S08alsasound': File exists
ln: creating symbolic link `/etc/rc5.d/S08alsasound': File exists
ln: creating symbolic link `/etc/rc6.d/K92alsasound': File exists
Building kernel modules for the 2.6.32-21-generic kernel, please wait... done.[/SIZE]
[CENTER]
----------------------------------------------------------
[SIZE=3][COLOR=DarkOrchid]**My Problem**[/COLOR][/SIZE]
Pictures shows my problem:
----------------------------------------------------------
[LEFT]
[/LEFT]
[/CENTER]
[SIZE=2][COLOR=Red]Ctrl+P:[/COLOR][/SIZE]
[CENTER]_[IMG]http://myup.ir/images/78095458288369505916.png[/IMG]_
[/CENTER]
[LEFT]
[/LEFT]
[SIZE=2][COLOR=Red]When I order a print command:[/COLOR][/SIZE]
[CENTER][IMG]http://myup.ir/images/60100190789196208019.png[/IMG]
[/CENTER]
[SIZE=4]
[SIZE=2][COLOR=Black]But, there isn't any printed page in output platform of my printer![/COLOR][/SIZE][/SIZE][SIZE=4][COLOR=Red][SIZE=2][COLOR=Black] The below photo shows contents of this path: [/COLOR][/SIZE][SIZE=1][COLOR=DarkOrchid]System/Administration/Printing/Printer/Ctrl+F[/COLOR][/SIZE]
[SIZE=2] After I ordered to print:[/SIZE][/COLOR][/SIZE]
[CENTER][IMG]http://myup.ir/images/33814074834037616052.png[/IMG]
[/CENTER]
 
[SIZE=2][COLOR=Red]Then => When I try to print a new page, Canon-LPB3100 printer is in this case:[/COLOR][/SIZE]
[CENTER][CENTER][IMG]http://myup.ir/images/46377394016153269677.png[/IMG]
[/CENTER]
 
***
[/CENTER]

I have another printer, too: [COLOR=DarkOrange]Samsun[/COLOR] ML-1640. I downloaded its driver from Samsung official website and install it. When I was installing the samsung driver, I got this Error:
```
Error: "/var/tmp/kdecache-identica" is owned by uid 1000 instead of uid 0.
```But installing process finished successfully! inside ML-1640 there is another one installed: CLP-300splc => Should I remove this one?
Samsung behaves like Canon: no print
[SIZE=2][COLOR=black] The below pictures shows the new conditions.

[COLOR=Red]Ctrl+P[/COLOR]
[/COLOR][/SIZE] [CENTER][IMG]http://myup.ir/images/80574712899260256842.png[/IMG]


[LEFT][SIZE=2][COLOR=Red]System/Administration/Printing/Printer[/COLOR][/SIZE][/LEFT]
  [IMG]http://myup.ir/images/03067948798569888221.png[/IMG]
[/CENTER]
 [SIZE=4][COLOR=Red][SIZE=2]
[COLOR=Black] But I can't print again[/COLOR][/SIZE][/COLOR][/SIZE]
[SIZE=2][COLOR=Black]there is no pulse to my printers.[/COLOR][/SIZE]  ](*,)

[SIZE=2][COLOR=Black]Pleas help me [-o<[/COLOR][/SIZE]

---

### Post by SidebySide on 2011-09-15
Bump

No Idea?
**It's in an urgency level for me! Please help me!**

---

### Post by SidebySide on 2011-09-27
> **SidebySide said:**
> Bump

No Idea?
**It's in an urgency level for me! Please help me!**
Bump a gain

---

### Post by SidebySide on 2011-10-09
[SIZE=1]I'm sorry for: «This topic is like a spam because of my "Bump"s»[/SIZE]

[SIZE=2][COLOR=Green]Help me plz.[/COLOR]
There's not any pulse toward the printer(Canon LBP3100B)! why?[/SIZE]
:(:confused:

---

