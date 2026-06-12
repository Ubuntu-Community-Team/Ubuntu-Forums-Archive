---
title: "Epson 4180 don't start"
date: 2009-06-11
forum: Hardware
---

### Post by gaver on 2009-06-11
Hi,

In Ubuntu 9.04, I have installed my Epson 4180 scanner following the information from Epson 4180 scanner (June 26the 2008).
 
scanimage -L
....
device `epson:libusb:001:005' is a Epson  flatbed scanner

lsusb
....
Bus 001 Device 005: ID 04b8:0118 Seiko Epson Corp. Perfection 4180 (GF-F600)

I use Xsane 0.996.

In scan and preview I get "Kon scanner niet aanzetten: Fout argument" "Can't start the scanner:Wrong argument"

What is this wrong argument, or what is missing.
Thanks in advance
gaver

---

### Post by Filiberke on 2009-07-02
[FONT=Arial][SIZE=2]Hi,[/SIZE][/FONT][SIZE=2]

[/SIZE]    [FONT=Arial][SIZE=2]I've had the same problem with my Agfa Scanwise e40. When i installed Ubuntu just about one month ago (yes, i'm a new linux user), it worked immediately with xsane. Didn't have to config anything.[/SIZE][/FONT][SIZE=2]

[/SIZE]    [FONT=Arial][SIZE=2]A few days ago when i wanted to use my scanner, starting up xsane gave me the following error: 'kon apparaat niet vinden 'snapscan:libusb:002:004': fout argument' or, in english: **'could not find device 'snapscan:libusb:002:004': wrong argument'**[/SIZE][/FONT][SIZE=2]

[/SIZE]    [FONT=Arial][SIZE=2]So i started browsing the forums and found alot of solutions involving permissions, but none of the m did something for me. You can try entering the** 'lsusb' , 'sane-find-scanner', and 'scanimage -L'** commands in the terminal, you will all see positive results. It is found, it is recognized, but it still doesn't work.[/SIZE][/FONT][SIZE=2]

[/SIZE]    [FONT=Arial][SIZE=2]Now try the following: just** type 'xsane' in the terminal**. I forgot to copy the actual error message you get in the terminal, but it involved the **'path to the firmware file of the scanner' being incorrect in the scanner-configuration file**. The location of that configuration file is also mentioned in the message, in my case it was /etc/sane.d/snapscan.conf ... but if you have another type of scanner, it will be different.[/SIZE][/FONT][SIZE=2]
[/SIZE]  [FONT=Arial][SIZE=2]
[/SIZE][/FONT] [FONT=Arial][SIZE=2]Now, you'll first have to **find that firmware-file of your specific scanner. It's a .bin file**, and it can be found on the install-CDrom of your scanner (even if it only contains windows-drivers), or in the driver package you can download from your scanner-manufacturer's website. In my case, i was lucky and just found the correct file immediately using google. Mine was called 'snape40.bin'.[/SIZE][/FONT][SIZE=2]
[/SIZE]  [FONT=Arial][SIZE=2]
[/SIZE][/FONT] [FONT=Arial][SIZE=2]Now copy this file into the folder /usr/share/sane[/SIZE][/FONT][SIZE=2]
[/SIZE]  [FONT=Arial][SIZE=2](command: sudo cp snape40.bin /usr/share/sane)[/SIZE][/FONT][SIZE=2]

[/SIZE]    [FONT=Arial][SIZE=2]Then go to the directory of the config file: command: cd /etc/sane.d[/SIZE][/FONT][SIZE=2]
[/SIZE]  [FONT=Arial][SIZE=2]Now open it to edit it: sudo gedit snapscan.conf  [/SIZE][/FONT][SIZE=2]
[/SIZE]  [FONT=Arial][SIZE=2](the conf file can have a different name with a different type of scanner, remember it from the error starting xsane)[/SIZE][/FONT][SIZE=2]
[/SIZE]  [FONT=Arial][SIZE=2]**In the config file, edit the line containing the link to the .bin file**, in my case it became:[/SIZE][/FONT][SIZE=2]
[/SIZE]  [FONT=Arial][SIZE=2]firmware /usr/share/sane/snape40.bin[/SIZE][/FONT][SIZE=2]
[/SIZE]  [FONT=Arial][SIZE=2]Then save & exit.[/SIZE][/FONT][SIZE=2]

[/SIZE]    [FONT=Arial][SIZE=2]If you have selected the correct .bin file, it will work. If you found several .bin files on your scanner-CD, try another one.[/SIZE][/FONT][SIZE=2]

[/SIZE]    [SIZE=2][I][FONT=Arial]But after all, the most important question remains: my scanner worked perfectly from the beginning, and after an automatic update this problem popped up. A problem that doesn't give a very clear error in the GUI. Why create all these troubles? My scanner worked fine without the .bin file... 
[/FONT][/I]
[/SIZE] [SIZE=2]*[FONT=Arial]Since i'm a new ubuntu user, this is the first 'solution' i write. I hope it'll be of some use to someone.[/FONT]*
[/SIZE] [SIZE=2][FONT=Arial][I][SIZE=2]
Greetings![/SIZE]
[/I][/FONT][/SIZE]

---

