---
title: "Ubuntu 64bit doesn't recognise all RAM"
date: 2013-01-01
forum: Hardware
---

### Post by JamesStewy on 2013-01-01
Hello,

I recently bought a new 2x4GB kit of RAM for my Toshiba M750 laptop (originally a 2x2GB kit of RAM) running Ubuntu Server 12.10. However, when I reinstalled from 32bit to 64bit, Ubuntu says I only have 3895MB of RAM instead of around 8000MB. 

So I looked around the internet for a bit and I found you could see the installed amount of RAM in the BIOS. When I checked it said I had 8192MB. To make sure my computer supported that much RAM I contacted Toshiba and they said it could.

On the internet I also found memtest86+. So I decided to run it and I got to Test 7 (Pass 44%) and I started getting millions of errors (About 7 million as I am writing this). 

Does anyone know why this is the case and possibly how to fix it?

Thanks,

JamesStewy

---

### Post by sudodus on 2013-01-01
> **JamesStewy said:**
> Hello,

I recently bought 4GB more RAM for my Toshiba M750 laptop (originally 4GB of RAM) running Ubuntu Server 12.10. However, when I reinstalled from 32bit to 64bit, Ubuntu says I only have 3895MB of RAM instead of around 8000MB. 

So I looked around the internet for a bit and I found you could see the installed amount of RAM in the BIOS. When I checked it said I had 8192MB. To make sure my computer supported that much RAM I contacted Toshiba and they said it could.

When recognized by the BIOS, the RAM should be recognized by Ubuntu (64-bit version)
> 

On the internet I also found memtest86+. So I decided to run it and I got to Test 7 (Pass 44%) and I started getting millions of errors (About 7 million as I am writing this). 

Does anyone know why this is the case and possibly how to fix it?

Thanks,

JamesStewy

According to my experience, when memtest complains, the RAM is bad. Or if you are lucky, there is a bad connection. If you wiggle the RAM cards a little, maybe they will connect better. Try that and run memtest again. If still bad, take out one RAM card each time to identify which one is bad and ask for it to be replaced.

---

### Post by JamesStewy on 2013-01-01
Hello,

Thanks for your help.

I will try that now.

JamesStewy

---

### Post by MrKrinkin on 2013-01-01
You are on a laptop. Chances are that the graphics card on your laptop uses some of the system memory and that is why not all 4GB is showing up.

I've got 8GB RAM on my laptop but 512mb is used by the GPU so I only get 7.5GB of usable system memory.

---

### Post by 2F4U on 2013-01-01
> **MrKrinkin said:**
> You are on a laptop. Chances are that the graphics card on your laptop uses some of the system memory and that is why not all 4GB is showing up.

I've got 8GB RAM on my laptop but 512mb is used by the GPU so I only get 7.5GB of usable system memory.

It is very unlikely that the graphics card uses half the RAM, since the OP upgraded from 4 GB to 8 GB of RAM.

> I recently bought 4GB more RAM for my Toshiba M750 laptop (originally  4GB of RAM) running Ubuntu Server 12.10. However, when I reinstalled  from 32bit to 64bit, Ubuntu says I only have 3895MB of RAM instead of  around 8000MB. 

---

### Post by JamesStewy on 2013-01-02
Hi MrKrinkin,

Thanks for your reply.

I fear I haven't explained myself correctly. I have 8gb of RAM installed in the computer but Ubuntu 64bit tells me I have around 4gb which is the amount I had before I bought some more.

Sudodus, I did as you recommended and ran memtest86+ on both sticks of RAM individually and they both started giving errors at a very specific time in the test. As far as I could work out, both sticks of RAM started giving errors at the start very start of Test #7.

Is there something worng with memtest86+? If it is right then both of my brand new sticks of RAM are faulty but the computer still runs fine? This doesn't make sense.

EDIT: I did some research on Test #7 specifically and it turns out to be an issue. In places I read claims that the memtest86+ on the Ubuntu 12.10 64 bit install CD (the one I use) is faulty and other places that it is a test which cheaper/slower RAM will almost certainly fail. Could this be why I am getting strange results?

---

### Post by greenfrog on 2013-01-02
You have two sticks of bad or wrong ram for you laptop.

Do a search for ram for your laptop model number with Google.

---

### Post by JamesStewy on 2013-01-02
But if they were two sticks of bad RAM, then why would Ubuntu install and work perfectly?

---

### Post by greenfrog on 2013-01-02
The bios is what tells the operating system how much ram is available.

How much ram does your bios show?

---

### Post by haqking on 2013-01-02
> **JamesStewy said:**
> But if they were two sticks of bad RAM, then why would Ubuntu install and work perfectly?

post output of

```
sudo dmidecode -t 17
```

---

### Post by haqking on 2013-01-02
> **greenfrog said:**
> The bios is what tells the operating system how much ram is available.

How much ram does your bios show?

The OP already answered that

---

### Post by JamesStewy on 2013-01-02
That is exactly what I thought.

The BIOS says I have 8192MB of RAM.

---

### Post by haqking on 2013-01-02
> **JamesStewy said:**
> That is exactly what I thought.

The BIOS says I have 8192MB of RAM.

post output of
```

sudo dmidecode -t 17
```

also

```
uname -m
```

to check you are running x64

---

### Post by JamesStewy on 2013-01-02
Hi, thanks for your reply.

```
sudo dmidecode -t 17
```

Outputs:

```
# dmidecode 2.11
SMBIOS 2.5 present.

Handle 0x0082, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0081
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 4096 MB
        Form Factor: SODIMM
        Set: Unknown
        Locator: DIMM 0
        Bank Locator: CSA 0 & 1
        Type: DDR2
        Type Detail: Synchronous
        Speed: 800 MHz
        Manufacturer: 7F7F
        Serial Number: 00000000
        Asset Tag: Not Specified
        Part Number:   K6451U64E6800F

Handle 0x0083, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0081
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 4096 MB
        Form Factor: SODIMM
        Set: Unknown
        Locator: DIMM 1
        Bank Locator: CSA 2 & 3
        Type: DDR2
        Type Detail: Synchronous
        Speed: 800 MHz
        Manufacturer: 7F7F
        Serial Number: 00000000
        Asset Tag: Not Specified
        Part Number:   K6451U64E6800F

```

and

```
uname -m
```

Outputs:

```
x86_64
```

---

### Post by haqking on 2013-01-02
> **JamesStewy said:**
> Hi, thanks for your reply.

```
sudo dmidecode -t 17
```Outputs:

```
# dmidecode 2.11
SMBIOS 2.5 present.

Handle 0x0082, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0081
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 4096 MB
        Form Factor: SODIMM
        Set: Unknown
        Locator: DIMM 0
        Bank Locator: CSA 0 & 1
        Type: DDR2
        Type Detail: Synchronous
        Speed: 800 MHz
        Manufacturer: 7F7F
        Serial Number: 00000000
        Asset Tag: Not Specified
        Part Number:   K6451U64E6800F

Handle 0x0083, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0081
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 4096 MB
        Form Factor: SODIMM
        Set: Unknown
        Locator: DIMM 1
        Bank Locator: CSA 2 & 3
        Type: DDR2
        Type Detail: Synchronous
        Speed: 800 MHz
        Manufacturer: 7F7F
        Serial Number: 00000000
        Asset Tag: Not Specified
        Part Number:   K6451U64E6800F

```and

```
uname -m
```Outputs:

```
x86_64
```


OK all looks good, where in Ubuntu is it reporting only 4gb ?

post output of

```
free
```

---

### Post by JamesStewy on 2013-01-02
All the commands I found on the internet to find the amount of RAM say around 4gb including free

Output:

```
             total       used       free     shared    buffers     cached
Mem:       3846480    1858660    1987820          0      68288    1183964
-/+ buffers/cache:     606408    3240072
Swap:      4882428          0    4882428

```

---

### Post by haqking on 2013-01-02
> **JamesStewy said:**
> All the commands I found on the internet to find the amount of RAM say around 4gb including free

Output:

```
             total       used       free     shared    buffers     cached
Mem:       3846480    1858660    1987820          0      68288    1183964
-/+ buffers/cache:     606408    3240072
Swap:      4882428          0    4882428

```

mmmmm ok.

I know this sounds bizarre, but remove the original DIMM to see if it sees the second on its own, also place the second in the original bank, you get the gist, process of elimination byt swapping DIMM configuration around in banks etc , though dmidecode is reporting fine.

---

### Post by JamesStewy on 2013-01-02
Ok Thanks. Will try tomorrow.

---

### Post by JamesStewy on 2013-01-02
> I know this sounds bizarre, but remove the original DIMM to see if it sees the second on its own, also place the second in the original bank, you get the gist, process of elimination byt swapping DIMM configuration around in banks etc , though dmidecode is reporting fine.

Upon re-reading my original post I fear I haven't explained my self well. I actually bought a brand new 2x4gb Kit and replaced the stock 2x2gb kit.

And, as recommended in the first reply on this thread, I tried every possible permutation of my two new sticks of RAM including one at a time. The result of all the tests were the BIOS reported the correct amount of RAM (4gb or 8gb depending if I had 1 or 2 sticks in at the time), Ubuntu always reported i had 4gb of RAM and memtest86+ worked up until the start of test #7 were i started getting millions of errors. 

The only potential reason I can think of at the moment is the integrated graphics isn't configured correctly and Ubuntu isn't realizing. This could be a potential issue as this is my old school laptop and I have no idea what the school may have done prior to me receiving it. This wouldb't have any thing to do with the operating system though as I have wiped the hard disk completely to remove windows and replace it with Ubuntu.

Is this possible?

JamesStewy

---

### Post by sudodus on 2013-01-03
> **JamesStewy said:**
> Upon re-reading my original post I fear I haven't explained my self well. I actually bought a brand new 2x4gb Kit and replaced the stock 2x2gb kit.

And, as recommended in the first reply on this thread, I tried every possible permutation of my two new sticks of RAM including one at a time. The result of all the tests were the BIOS reported the correct amount of RAM (4gb or 8gb depending if I had 1 or 2 sticks in at the time), Ubuntu always reported i had 4gb of RAM and memtest86+ worked up until the start of test #7 were i started getting millions of errors. 

The only potential reason I can think of at the moment is the integrated graphics isn't configured correctly and Ubuntu isn't realizing. This could be a potential issue as this is my old school laptop and I have no idea what the school may have done prior to me receiving it. This wouldb't have any thing to do with the operating system though as I have wiped the hard disk completely to remove windows and replace it with Ubuntu.

Is this possible?

JamesStewy
You have really tried to do the right things, and yet no luck.

Just a quick check. Is this link describing your computer?
[[COLOR="Red"]http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&toshibaShop=true&com.broadvision.session.new=Yes&PRODUCT_ID=1058973[/COLOR]]("http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&toshibaShop=true&com.broadvision.session.new=Yes&PRODUCT_ID=1058973")
In that case it should manage with 8 GB RAM. Furthermore it states  DDR2 RAM (800 MHz).

Check with the following command, that your memory sticks have the correct specs. 
```
sudo lshw -class memory
```

I suggest that you check also with the original memory sticks, if lshw will display the same or some other ratings, for example clock speed (800 MHz in Toshiba's specs).
--
Toshiba writes the following in the specs

Graphics adaptor    type : Mobile Intel® GMA 4500MHD  
  memory : up to 1,340 MB total available graphics memory with 4 GB system memory  
  memory type : shared 

and we may ask: what happens with more than 4 GB of memory?

I wouldn't blame the graphics card or graphics driver yet, but who knows for sure.

***Try when booted from an Ubuntu install CD/DVD/USB drive without any proprietary driver installed!***

---

### Post by JamesStewy on 2013-01-03
Yes that is the correct laptop. Although i don't know if there are differences between different countries (I live in Australia).

I did a lot of research into compatibility of RAM before purchasing. I actually looked up the RAM which was pre-installed in the computer and got a word-for-word copy of it except it was twice the capacity. Your terminal command backed that up.

I may be missing something but if there was an issue with the RAM (say faulty or incompatible) wouldn't Ubuntu have issues (maybe not even start)?

> Try when booted from an Ubuntu install CD/DVD/USB drive without any proprietary driver installed!

Do you mean I use Ubuntu LiveCD and see if it detects the right amount of RAM? 

JamesStewy

---

### Post by sudodus on 2013-01-03
> **JamesStewy said:**
> ...

I may be missing something but if there was an issue with the RAM (say faulty or incompatible) wouldn't Ubuntu have issues (maybe not even start)?

That's what I'd expect too. But ...
> 

Do you mean I use Ubuntu LiveCD and see if it detects the right amount of RAM? 

JamesStewy
Yes! And try also another Ubuntu version (10.04 ... 12.10) or another linux distro, for example Knoppix (live).

---

### Post by JamesStewy on 2013-01-03
Ok. So I tried two LiveCDs.

First I used 12.04 and when I ran uname -m it reported a 32 bit system. 

Then I downloaded 10.04 LiveCD and tried that. I ran uname -m again at it reported a 64 bit system :). But I then ran free and it reported the same amount of RAM as 12.10 did (around 4gb) :(.

JamesStewy

---

### Post by sudodus on 2013-01-04
What about the 12.04 32-bit system: If it has pae (physical address extension), it can manage more than 4 GB ram, although not as efficiently as a 64-bit system. At least check with it (and let us know, please) what size of memory it reports. See for example this link

[http://wiki.openvz.org/Different_kernel_flavors_%28UP,_SMP,_ENTERPRISE,_ENTNOSPLIT%29]("http://wiki.openvz.org/Different_kernel_flavors_%28UP,_SMP,_ENTERPRISE,_ENTNOSPLIT%29")

I think a check with another linux distro will show, if this is an Ubuntu specific problem or not. Knoppix is based on Debian. I guess you can test a non-debian distro too, for example Fedora (sponsored by Red Hat).

Once again, can you identify anything in the bios menu system to tweak in order to make all the memory available to the OS?

---

### Post by JamesStewy on 2013-01-04
Running free on 12.04 LiveCD (32 bit) outputs 3895MB.

Running free on the latest Fedora LiveCD outputs 3895MB.

No I haven't found found anything in the BIOS, just the memory amount.

Is it possible it is using 8gb of RAM but just not reporting it?

---

### Post by sudodus on 2013-01-04
> **JamesStewy said:**
> Running free on 12.04 LiveCD (32 bit) outputs 3895MB.

Running free on the latest Fedora LiveCD outputs 3895MB.

No I haven't found found anything in the BIOS, just the memory amount.

Is it possible it is using 8gb of RAM but just not reporting it?

Now we know, that the problem is not only for Ubuntu. I don't know, but I would be very surprised if [FONT="Courier New"][SIZE="3"]free[/SIZE][/FONT] would not report all the RAM available for the operating system.

I wonder if there is any way to check how much of the RAM that is allocated for the graphics. And I wonder why memtest is getting all these errors. It seems to me, that there is something very fundamentally bad in the management of RAM above 4 GB, I mean something in the computer hardware or BIOS, not in the operating system.

---

### Post by sudodus on 2013-01-04
> **JamesStewy said:**
> 
Is there something worng with memtest86+? If it is right then both of my brand new sticks of RAM are faulty but the computer still runs fine? This doesn't make sense.

EDIT: I did some research on Test #7 specifically and it turns out to be an issue. In places I read claims that the memtest86+ on the Ubuntu 12.10 64 bit install CD (the one I use) is faulty and other places that it is a test which cheaper/slower RAM will almost certainly fail. Could this be why I am getting strange results?

I didn't see this edit before. Interesting, another source of error, or source of knowledge ...

- Do the old RAM sticks pass this test #7?

- What about running memtest with 12.04?

- Are the new RAM sticks 4 GB each while the old ones are 'only' 2 GB each? Could it be, that there is some addressing problem for single sticks of 4 GB?

- Is the memtest result depending on which slot(s) you are using? (where the RAM sticks are plugged in)

---

### Post by JamesStewy on 2013-01-04
> **sudodus said:**
> I didn't see this edit before. Interesting, another source of error, or source of knowledge ...

- Do the old RAM sticks pass this test #7?

- What about running memtest with 12.04?

- Are the new RAM sticks 4 GB each while the old ones are 'only' 2 GB each? Could it be, that there is some addressing problem for single sticks of 4 GB?

- Is the memtest result depending on which slot(s) you are using? (where the RAM sticks are plugged in)

- They fail on Test #7

- Yes that is correct. I don't know? I would have though there would be no issue seeing that 4gb is relatively common.

- No. I tried every posible permutation of RAM, RAM amount (1 or 2 at a time) and slot and they all failed at the start of Test #7.

JamesStewy

---

### Post by sudodus on 2013-01-04
> **JamesStewy said:**
> - They fail on Test #7

- Yes that is correct. I don't know? I would have though there would be no issue seeing that 4gb is relatively common.

- No. I tried every posible permutation of RAM, RAM amount (1 or 2 at a time) and slot and they all failed at the start of Test #7.

JamesStewy
It seems memtest #7 is buggy, and we should not pay too much attention to it. But the problem is still there, that your linux system does not see more than 4 GB of RAM. Sorry, I have no more ideas right now.

---

### Post by haqking on 2013-01-04
You had this problem back in September with 12.04 according to the following link

[http://askubuntu.com/questions/187200/pae-on-ubuntu-12-04](http://askubuntu.com/questions/187200/pae-on-ubuntu-12-04)

I am guessing it is a BIOS related issue not reporting correct memory to OS but who knows, if you have had this issue this long with 2 different OS versions and live CD, 32 bit PAE and x64 then the problem is hardware.

Are you running latest firmware, BIOS ?

This is not an OS issue

Peace

---

### Post by JamesStewy on 2013-01-04
I totally agree with you haqking, I don't think it is a OS issue, or an issue with the RAM itself.

Now that I think about it, these two issues maybe related as you alluded to. 

I checked my BIOS version and it turns out I have version 1.3 and the latest is 3.0. However, when I went to the  [_Toshiba Downloads Page_]("http://www.mytoshiba.com.au/support/computers/portege/m750/ppm75a-01g010/download?os=25") I found a problem. The BIOS upgrade only came in a .exe. So I downloaded it anyway and tried to use wine to run it. This only ended in a load of errors.

Is there a way to upgrage the BIOS without Windows?

JamesStewy

---

### Post by haqking on 2013-01-04
> **JamesStewy said:**
> I totally agree with you haqking, I don't think it is a OS issue, or an issue with the RAM itself.

Now that I think about it, these two issues maybe related as you alluded to. 

I checked my BIOS version and it turns out I have version 1.3 and the latest is 3.0. However, when I went to the  [_Toshiba Downloads Page_]("http://www.mytoshiba.com.au/support/computers/portege/m750/ppm75a-01g010/download?os=25") I found a problem. The BIOS upgrade only came in a .exe. So I downloaded it anyway and tried to use wine to run it. This only ended in a load of errors.

Is there a way to upgrage the BIOS without Windows?

JamesStewy

you will need to use a FreeDOS boot disk or similar, you cant flash BIOS through WINE.

[http://goebelmeier.de/bootstick/](http://goebelmeier.de/bootstick/)

or on CD [http://www.freedos.org/download/](http://www.freedos.org/download/)

---

### Post by JamesStewy on 2013-01-04
I think you are going to have to elaborate on what I have to do - n00b alert :)

On the FreeDOS website they said it is an OS and will install over existing OS?

Would it just be easier (and safer) to install a windows 7 trail along side Ubuntu and run the update through that?

---

### Post by haqking on 2013-01-05
> **JamesStewy said:**
> I think you are going to have to elaborate on what I have to do - n00b alert :)

On the FreeDOS website they said it is an OS and will install over existing OS?

Would it just be easier (and safer) to install a windows 7 trail along side Ubuntu and run the update through that?

no it is a bootdisk

---

### Post by JamesStewy on 2013-01-05
> no it is a bootdisk

Sorry. What specifically is the bootdisk that you are referring to. The exe that I downloaded from Toshiba looks like a file you run on Windows that updates the BIOS. Not like a ISO or something you burn to a CD or put on a USB drive. 

I am sorry if I am not helping but this area is stretching my knowledge and might need extra explaining.

Thanks,

JamesStewy

---

### Post by haqking on 2013-01-05
> **JamesStewy said:**
> Sorry. What specifically is the bootdisk that you are referring to. The exe that I downloaded from Toshiba looks like a file you run on Windows that updates the BIOS. Not like a ISO or something you burn to a CD or put on a USB drive. 

I am sorry if I am not helping but this area is stretching my knowledge and might need extra explaining.

Thanks,

JamesStewy

the first link i posted is how to cerate a dos boot disk (that you boot to) you are then in DOS allowing you to update your BIOS
from the page i linked to title:

> **Creating FreeDOS USB boot stick for BIOS flashing**



---

### Post by Rsjc741 on 2013-01-06
James, it may help to look up how DOS has progressed from the 1980's - Today.

Here's a little bit of the facts though:

mid-late 80's, Microsoft used its own version of DOS (MS-DOS), as a starting platform for Windows. What I mean by that is that Windows ran on top of DOS.

By the 90's, Windows was still being made to run on top of DOS, albeit with some more features from the MS-DOS 3.11 days

Windows 95 was the last MS-DOS based OS produced by Microsoft. Windows 98 and NT ran on the Windows NT kernel

I'm sure that if you were older that 5 in the 90's and early 2000's, you remember that horrible-looking "MS DOS" icon.

Yeah, this one:
[IMG]http://www.geekosystem.com/wp-content/uploads/2011/07/ms-dos-logo1.jpg[/IMG]

That was to revert back to the MS-DOS shell. Mainly for 16-bit backwards compatibility.



As for your problem.. it's probably a BIOS issue, or an issue with the North Bridge itself. (The controller that links the CPU to the Memory banks)

I believe 3.865Gb of RAM is the magic number for the max amount of memory a 32-bit system can hold.

Er, just for SnG... Is IOMMU turned on? What about 32-bit to 64-bit conversion in IOMMU?

I would get memory errors if I had either of those turned off.

The latter is also specific for Linux-based OS's. Or so my BIOS tells me. (Asus M5A97)

---

### Post by JamesStewy on 2013-01-06
Ok, Thanks.

I tried the instructions on the first link ([http://goebelmeier.de/bootstick/](http://goebelmeier.de/bootstick/)) and I pressed enter on step #8 then I got the following screen (attached) which isn't the 'Set the Time' screen the instructions say would follow in step #9.

The files structure of the USB is as follows:
```
G:\
&#9474;   command.com
&#9474;   fat32lba.bss
&#9474;   kernel.sys
&#9474;   syslinux.cfg
&#9474;
&#9500;&#9472;&#9472;&#9472;flash
&#9474;       bios.exe
&#9474;
&#9492;&#9472;&#9472;&#9472;odin
    &#9474;   add.com
    &#9474;   append.exe
    &#9474;   assign.com
    &#9474;   attrib.com
    &#9474;   autoexec.bat
    &#9474;   bookshlf.exe
    &#9474;   bootfix.com
    &#9474;   callver.com
    &#9474;   cd2iso86.exe
    &#9474;   cdrcache.sys
    &#9474;   chkdsk.exe
    &#9474;   choice.exe
    &#9474;   cmd8086.com
    &#9474;   comp.com
    &#9474;   cpulevel.com
    &#9474;   ctmouse.exe
    &#9474;   cwsdpmi.exe
    &#9474;   debug.com
    &#9474;   defrag.exe
    &#9474;   defrag.hlp
    &#9474;   deltree.com
    &#9474;   devload.com
    &#9474;   diskcomp.com
    &#9474;   diskcopy.exe
    &#9474;   diskcopy.ini
    &#9474;   disk_sim.cfg
    &#9474;   display.exe
    &#9474;   dosfsck.exe
    &#9474;   drvon.com
    &#9474;   du.exe
    &#9474;   edit.cfg
    &#9474;   edit.exe
    &#9474;   edit.hlp
    &#9474;   edlin.exe
    &#9474;   emm386.exe
    &#9474;   fc.exe
    &#9474;   fdapm.com
    &#9474;   fdconfig.sys
    &#9474;   fdisk.exe
    &#9474;   fdisk.ini
    &#9474;   fdiskpt.ini
    &#9474;   fdpkg.exe
    &#9474;   find.com
    &#9474;   fips.doc
    &#9474;   fips.exe
    &#9474;   format.exe
    &#9474;   freetest.com
    &#9474;   getline.com
    &#9474;   graph-hp.com
    &#9474;   graph-ps.com
    &#9474;   graphpin.com
    &#9474;   help.com
    &#9474;   help.exe
    &#9474;   himem.exe
    &#9474;   index.htm
    &#9474;   iniadd.com
    &#9474;   keyb.exe
    &#9474;   keyboard.sys
    &#9474;   keybrd2.sys
    &#9474;   keybrd3.sys
    &#9474;   label.exe
    &#9474;   lbacache.com
    &#9474;   lfn2sfn.exe
    &#9474;   localize.com
    &#9474;   locate.com
    &#9474;   md5sum.exe
    &#9474;   mem.exe
    &#9474;   meta-all.bin
    &#9474;   metaboot.bot
    &#9474;   mode.com
    &#9474;   more.exe
    &#9474;   moresys.sys
    &#9474;   move.exe
    &#9474;   nansi.sys
    &#9474;   oscheck.com
    &#9474;   part.exe
    &#9474;   partsimp.exe
    &#9474;   pbatch.exe
    &#9474;   pg.exe
    &#9474;   replace.exe
    &#9474;   rerror.com
    &#9474;   restorrb.exe
    &#9474;   ripcord.exe
    &#9474;   sfn2lfn.exe
    &#9474;   share.com
    &#9474;   shfdrv86.exe
    &#9474;   shrdrv86.exe
    &#9474;   shsucdhd.exe
    &#9474;   shsucdx.com
    &#9474;   shsufdrv.exe
    &#9474;   shsurdrv.exe
    &#9474;   spfdisk.exe
    &#9474;   svtxt.com
    &#9474;   sys.com
    &#9474;   tickle.com
    &#9474;   tree.com
    &#9474;   unzip.exe
    &#9474;   whichfat.com
    &#9474;   xcopy.exe
    &#9474;   xdel.exe
    &#9474;   xdma.sys
    &#9474;   xfdisk.exe
    &#9474;   xfdisk.ini
    &#9474;   xmssize.com
    &#9474;
    &#9500;&#9472;&#9472;&#9472;cpi
    &#9474;       ega.cpx
    &#9474;       ega10.cpx
    &#9474;       ega2.cpx
    &#9474;       ega3.cpx
    &#9474;       ega4.cpx
    &#9474;       ega5.cpx
    &#9474;       ega6.cpx
    &#9474;       ega7.cpx
    &#9474;       ega8.cpx
    &#9474;       ega9.cpx
    &#9474;
    &#9492;&#9472;&#9472;&#9472;help
        &#9474;   fdl.txt
        &#9474;   index.htm
        &#9474;
        &#9500;&#9472;&#9472;&#9472;docinfo
        &#9474;   &#9492;&#9472;&#9472;&#9472;bi
        &#9474;       &#9492;&#9472;&#9472;&#9472;nls
        &#9474;               en.bi
        &#9474;
        &#9500;&#9472;&#9472;&#9472;en
        &#9474;   &#9474;   help.htm
        &#9474;   &#9474;   index.htm
        &#9474;   &#9474;
        &#9474;   &#9492;&#9472;&#9472;&#9472;hhstndrd
        &#9474;           h2cpying.txt
        &#9474;           hhstndrd.zip
        &#9474;           readme.1st
        &#9474;
        &#9492;&#9472;&#9472;&#9472;ru
            &#9492;&#9472;&#9472;&#9472;hhstndrd
                    edit.htm

```

> Er, just for SnG... Is IOMMU turned on? What about 32-bit to 64-bit conversion in IOMMU?

I don't understand. Can you please elaborate.

Thanks

JamesStewy

---

### Post by JamesStewy on 2013-01-07
Ok. It turns out there was something wrong with the USB I tired.

Once I got a new USB, I re-did the steps and I got to step #9, hit enter twice to skip the time setting then it entered me into a DOS shell. In the DOS shell I changed the directory to the "flash" folder. Then, I typed bios.exe (the file I downloaded from Toshiba) and I got an error saying:

> This file needs to be run under Win32

The USB has the same file tree as listed in my previous post and is formatted to FAT32.

Does this mean I have to install a 32bit version of Windows just to run a BIOS update?

Thanks

JamesStewy

---

### Post by sudodus on 2013-01-07
An alternative is to get ***'BartPE'*** or ***'WinPE'***. PE means Preinstallation Environmenet, and these are tools for tasks like yours, when FAT or NTFS needs chkdsk /f, and others, when some Windows tools are necessary, but you don't have a [working] Windows installed in the computer.

You will find information on the internet how to download tools to create such PEs.

[http://www.nu2.nu/pebuilder/]("http://www.nu2.nu/pebuilder/")

[https://en.wikipedia.org/wiki/Windows_Preinstallation_Environment]("https://en.wikipedia.org/wiki/Windows_Preinstallation_Environment")

---

### Post by JamesStewy on 2013-01-07
As I understand this, BartPE will create a windows XP LiveCD which will allow me to run the Toshiba BIOS upgrade. Is this correct?

If so I will try this tomorrow.

---

### Post by sudodus on 2013-01-07
> **JamesStewy said:**
> As I understand this, BartPE will create a windows XP LiveCD which will allow me to run the Toshiba BIOS upgrade. Is this correct?

If so I will try this tomorrow.
- A very small and simple live CD/USB drive, with only what is necessary for repair tasks or inspection tasks, yes.

It does run in graphics mode, so you can install and run GUI programs like for example Total Commander.

---

### Post by JamesStewy on 2013-01-08
SOLVED.

Firstly, I just want to thank everyone who posted on this thread. I am staggered by the help I received and I have no doubt in my mind that I wouldn't have solved it without you.

I had a very long day yesterday but this is what happened. 

I firstly tried to make a BartPE LiveCD however, after numerous tweaks with different plugins I was unable to start it on my Toshiba laptop. The issue I faced was a black screen and no activity (hard drive, CD drive, nothing) just after it checked the hardware configuration. However, I was able to run it further on my new Fujitsu laptop but it got a blue screen (of death :() just after the XP splash screen.

After looking on the internet I found Win7PE (not to be confused with WinPE which is Microsoft's version) which claimed to have less compatibility issues. Following this great tutorial ([http://www.irongeek.com/i.php?page=security/winbuilder-win7pe-se-tutorial](http://www.irongeek.com/i.php?page=security/winbuilder-win7pe-se-tutorial)) I was able to create a Windows 7 LiveCD. This I had more success with as I was able to completely boot into Windows 7. However, upon running the Toshiba BIOS updater exe I got a weird error message saying:
> Unable to execute the executable! 

I looked it up on the Internet and found nothing. After a lot more searching I found a page on the German Toshiba site (I lost the link) which listed all the updates to the BIOS and what the changed for my particular laptop. Under the 1.6 update it said:
> Increased support for 8gb or more RAM for Windows Vista
Hoping that this was the solution, I found a legacy download for version 1.6 ([http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/downloadDetail.jsp?pf=true&soid=2290142](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/downloadDetail.jsp?pf=true&soid=2290142)). This download turned out different to the version 3.0 download as it gave three options to update the BIOS.
[LIST=1]
[*]Create a bootable Diskette
[*]Create a bootable CD/DVD
[*]Update through Windows
[/LIST]
This ended up being the solution as I was able to create a bootable CD, update the BIOS, and bring 8gb support to Ubuntu. Free now outputs:
```
             total       used       free     shared    buffers     cached
Mem:       7975248    2024360    5950888          0     190664     720660
-/+ buffers/cache:    1113036    6862212
Swap:      4882428          0    4882428

```

Again I would like to thank everyone who posted for their unbelievable support on this thread.

Thanks,

JamesStewy

---

### Post by haqking on 2013-01-08
> **JamesStewy said:**
> SOLVED.

Firstly, I just want to thank everyone who posted on this thread. I am staggered by the help I received and I have no doubt in my mind that I wouldn't have solved it without you.

I had a very long day yesterday but this is what happened. 

I firstly tried to make a BartPE LiveCD however, after numerous tweaks with different plugins I was unable to start it on my Toshiba laptop. The issue I faced was a black screen and no activity (hard drive, CD drive, nothing) just after it checked the hardware configuration. However, I was able to run it further on my new Fujitsu laptop but it got a blue screen (of death :() just after the XP splash screen.

After looking on the internet I found Win7PE (not to be confused with WinPE which is Microsoft's version) which claimed to have less compatibility issues. Following this great tutorial ([http://www.irongeek.com/i.php?page=security/winbuilder-win7pe-se-tutorial](http://www.irongeek.com/i.php?page=security/winbuilder-win7pe-se-tutorial)) I was able to create a Windows 7 LiveCD. This I had more success with as I was able to completely boot into Windows 7. However, upon running the Toshiba BIOS updater exe I got a weird error message saying:
 

I looked it up on the Internet and found nothing. After a lot more searching I found a page on the German Toshiba site (I lost the link) which listed all the updates to the BIOS and what the changed for my particular laptop. Under the 1.6 update it said:

Hoping that this was the solution, I found a legacy download for version 1.6 ([http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/downloadDetail.jsp?pf=true&soid=2290142](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/downloadDetail.jsp?pf=true&soid=2290142)). This download turned out different to the version 3.0 download as it gave three options to update the BIOS.
[LIST=1]
[*]Create a bootable Diskette
[*]Create a bootable CD/DVD
[*]Update through Windows
[/LIST]
This ended up being the solution as I was able to create a bootable CD, update the BIOS, and bring 8gb support to Ubuntu. Free now outputs:
```
             total       used       free     shared    buffers     cached
Mem:       7975248    2024360    5950888          0     190664     720660
-/+ buffers/cache:    1113036    6862212
Swap:      4882428          0    4882428

```Again I would like to thank everyone who posted for their unbelievable support on this thread.

Thanks,

JamesStewy


So it was BIOS, thought so.

Cool, glad you got it sorted.

Peace

---

### Post by sudodus on 2013-01-08
> **haqking said:**
> So it was BIOS, thought so.

Cool, glad you got it sorted.

Peace
+1

Congratulations to a good job, JamesStewy :KS

---

