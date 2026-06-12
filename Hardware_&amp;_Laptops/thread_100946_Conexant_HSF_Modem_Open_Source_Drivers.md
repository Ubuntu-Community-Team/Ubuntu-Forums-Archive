---
title: "Conexant HSF Modem Open Source Drivers"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by MistaED on 2005-12-08
Hello, I'd like to ask about this driver:
[https://wiki.ubuntu.com/forum/hardware/Conexant](https://wiki.ubuntu.com/forum/hardware/Conexant)

The one Alexandre Strube/Rafael Espíndola ported to the ubuntu/linux kernel 2.6.12. Where can I get more information on this like the name of the module so I can modprobe it and get GnomePPP to work with it? I cannot find any info on this, is it really in the kernel already, how do I put in the hsf part? I checked lspci with it and the chipset/card is identical.

Thanks
-MistaED

---

### Post by coolclassic on 2005-12-09
you will get more info here re conexant but be aware for the full version you will have to pay, it may be cheaper to buy a new modem from ebay. The trial version restricts speeds to 14bps. 

[http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)

---

### Post by edemark on 2005-12-09
please google a wiki page searching for installing rh9 on compaq nx9010. The page explains how to make the modem work full speed with the driver of linuxant.

Personally I bought my notebook with mdk 9.2 thus i was upset that i did not get a full speed modem driver with my new machine. I do think that it is unjust that you buy your pc with linux and they sell it to you without having free linux driver (or propietary but its price included in the price of the pc).

good luck

---

### Post by lance bermudez on 2006-02-09
im new to linux and i can not seem to find the page you said to look for could you provide a link please.

---

### Post by az on 2006-02-09
[QUOTE=MistaED]Hello, I'd like to ask about this driver:
[https://wiki.ubuntu.com/forum/hardware/Conexant](https://wiki.ubuntu.com/forum/hardware/Conexant)

The one Alexandre Strube/Rafael Espíndola ported to the ubuntu/linux kernel 2.6.12. Where can I get more information on this like the name of the module so I can modprobe it and get GnomePPP to work with it? I cannot find any info on this, is it really in the kernel already, how do I put in the hsf part? I checked lspci with it and the chipset/card is identical.

Thanks
-MistaED[/QUOTE]
I just looked at that.

Long ago, before linuxant was in business, two guys from Montreal (Marc Boucher and another person, I beleive) started a project to get the conexant chipset modems  to work in linux.  During the development, they provided their driver for free.  It was not open source, since they used a precompiled binary they got from Conexant.

This is the old, free 2.4 kernel driver for conexant chipsets.  Just before the 2.6 kernel was released, they ported it to the 2.6 kernel and closed the project, and started to charge money for it.  They became Linuxant. 

The project you refer to above is a copy of that original free, beta driver, which has been ported to the 2.6 kernel.  The precompiled binary part is still there.  It is proprietary and not open source.  It is also something like three years old and may not work with newer modems.  I am not sure about how legal it is to distribute the proprietary object files.

So, no, it will never become part of the kernel unless they release that precompiled binary as free-libre open source software.

These are the object files in question from the driver package:
dora@dora:~/Desktop$ ls conexant/modules/imported/
hsfali.O  hsfbasic2.O  hsfengine.O  hsfich.O  hsfvia.O  hsfyukon.O  include

---

### Post by lance bermudez on 2006-03-12
Installing RH9 on a Compaq nx9010 laptop - FreaxWiki
[http://freax.be/wiki/index.php/Installing_RH9_on_a_Compaq_nx9010_laptop](http://freax.be/wiki/index.php/Installing_RH9_on_a_Compaq_nx9010_laptop)

---

### Post by frankabel on 2007-01-20
> **lance bermudez said:**
> Installing RH9 on a Compaq nx9010 laptop - FreaxWiki
[http://freax.be/wiki/index.php/Installing_RH9_on_a_Compaq_nx9010_laptop](http://freax.be/wiki/index.php/Installing_RH9_on_a_Compaq_nx9010_laptop)

That link show a empty page. Can anybody tell me where find get work my modem? (laptop compaq nx9010)

Salute
Frank Abel

---

### Post by loko on 2007-02-11
no problem, dude

> It's a Conexant 56k ACLink Modem and located on PCI 0:8:0, man lspci for more info.

Note from Germán Sanchis Trilles: The winmodem works perfectly using the hsf (softmodem) driver from linuxant. You can find this driver in [[http://www.linuxant.com/drivers/hsf/index.php](http://www.linuxant.com/drivers/hsf/index.php) [www.linuxant.com/](www.linuxant.com/) drivers/ hsf/ index.php]. Since I use debian and neither my distribution nor me feel too confident with rpms, I haven't tried the rpm package, I installed it with the tar.gz package. Read the README file for instructions about how to install the driver, they are quite clear. After the installation, the modem should be accessible at /dev/ttySHSF0 or at /dev/modem, the latter one being a symbolic link of the former one.

Note from Philip Van Hoof: I have tested the RPM package hsfmodem-6.03.00lnxt03091800free-1.i386.rpm and verify that this package works. It also works on a patched kernel (see below at ACPI support). You can find this file here: [[http://www.linuxant.com/drivers/hsf/free/downloads.php](http://www.linuxant.com/drivers/hsf/free/downloads.php) [www.linuxant.com/](www.linuxant.com/) drivers/ hsf/ free/ downloads.php].

Output of hsfconfig --info:

Config for modem unit 0: /dev/ttySHSF0
        Device instance: 0-PCI-10b9:5457-103c:0850
        HW revision    : CXT29
        HW profile name: hsfmc97ali
        Current region : BELGIUM (T.35 code: 000F)

The /dev/modem alias (symlink) points to /dev/ttySHSF0

Note from Lamarque Souza: Use this key regenerator to make the linuxant driver work at full speed in 2.6 kernels:

wget [http://www.geocities.com/booboohoot/generator.pl](http://www.geocities.com/booboohoot/generator.pl)
chmod 755 generator.pl
./generator.pl <License owner> <Registration ID>

You can get the License owner and Registration ID with

hsfconfig --info

The key generated should enable full modem functionality (including full speed and fax). I have not tested the modem as fax so do not ask me it really works. If the key generator does not work (it does not work with the latest driver, hsfmodem-7.18.00full.tar.gz) use the hack below. This hack does not enable fax functionality.

Note from Lamarque: I use version 7.18 of the driver. I do not have hsfmodem-6.03.00lnxt04082400full.tar.gz or a key generator for driver version 7.x. Please do not ask me for any of them. Use the hack if you want to user driver version 7.x.

To hack the driver just use hexedit to replace the 74 number to 75 at offset 0x248cd of hsfmodem-6.03.00lnxt04051300full/modules/imported/hsfengine-i386.O or /usr/lib/hsfmodem/modules/imported/hsfengine-i386.O (if the driver is already installed):

hexedit hsfmodem-6.03.00lnxt04051300full/modules/imported/hsfengine-i386.O

Press ENTER, type 248cd, press ENTER, type 75, press ENTER, press Ctrl+X, 
type Y, press ENTER.

The offset 0x248cd will be different if you use a driver other than hsfmodem-6.03.00lnxt04051300full.tar.gz. The offset of driver hsfmodem-6.03.00lnxt04082400full.tar.gz is 0x2488D. The offset of the latest driver (hsfmodem-7.18.00full.tar.gz) is 0x2659D.

I had a memory leak in my notebook caused by an infinite loop in modprobe (in modules.dep hsfserial depends on hsfmc97ali and vice-versa). The memory leak seems to be solved in version 7.18. To prevent the memory leak edit hsfmodem-6.03.00lnxt04051300full/scripts/hsfconfig or /usr/sbin/hsfconfig (if the driver is already installed), change the lines below from:

echo "probeall /dev/ttySHSF hsfpcibasic2 hsfmc97ich hsfmc97via hsfmc97ali"
echo "probeall hsfserial hsfpcibasic2 hsfmc97ich hsfmc97via hsfmc97ali"

To

echo "probeall /dev/ttySHSF hsfpcibasic2 hsfmc97ali"

Execute

cd hsfmodem-6.03.00lnxt04051300full
make install
hsfconfig
 


And also this:

> In the same forum where I found this hack there is also a post of a patch to enable full speed driver with kernel 2.6. I have not tested it since mine is already in full speed. :-)

Note from Milton Paiva Neto: To get the modem working at maximum speed, download the file [www.meumaterial.hpg.com.br/](www.meumaterial.hpg.com.br/) modem/ dell-hsflinmodem-5.03.27.tar.gz in a tmp directory  :Note from jt :This site no longer works.Why steal in linux

#tar -zxvf dell-hsflinmodem-5.03.27.tar.gz

will be created three directories(dell,etc,usr), type i

# cd usr/src/hsflinmodem
# tar -zxvf hsflinmodem-5.03.27lnxtbeta03041600.tar.gz

Change to the created directory

# cd hsflinmodem-5.03.27lnxtbeta03041600

If you have any previous version of this modem driver you will need to remove the old driver, to remove type

# rpm -el hsflinmodem or make uninstall

now that you have uninstalled the driver, install the new one

# make install

The driver will be installed, you will get the message telling that the modem were installed, now type

# hsfconfig

Type 'yes' for automatic detection: yes
Type the name of your country (if exist in the list):BRAZIL
Type the path of your kernel source (depends on your kernelversion): /lib/modules/2.4.20-8custom/build
Note from Philip Van Hoof: To know what path you need, try echo "/lib/modules/`uname -r`/build"
ps. I recompiled my kernel for ACPI and NTFS support using the instructions on this site.

Congratulations your modem has been configured, enjoy it at 56k!

Feel free to contribute additional information or mail me in case of problems (see below).


Note from Peter Scott:

Fedora core == 1
I had to edit the serial_core.c file inorder to get hsfconfig to be able to compile the driver corectly. to do this:

edit the file 
hsf/usr/src/hsflinmodem/hsflinmodem-5.03.27lnxtbeta03041600/modules/serial_
core.c
and change line 1073 from
if ((tty->count == 1) && (state->count != 1)) {
to
if (((tty->count.counter) == 1) && (state->count != 1)) {

then run make install followed by /usr/sbin/hsfconfig

Note From Ow(Ow.Mun.Heng_at_nospam_wdc_com)

RH9 + Kernel 2.4.23+cpufreq_patch) Tried compiling it.. This one can be compiled as is.. (i think, I'm lazy to re-compile it) After a few tries.. I vi the modules/makefile and just uncommented line 41


   1. Remove the following if your OS already has the new serial core
   2. (expected to be merged one day in linux 2.5) 

serial_hsf.o: CFLAGS += -DCNXTSERIAL_INCLUDE_CORE <---uncommented

   1. The following is a workaround as the previous line causes certain
   2. versions of GNU make to crash with the message:
   3. "make: expand.c:489: allocated_variable_append: Assertion 

`current_variable_set_list->next != 0' failed."

   1. CFLAGS-serial_hsf = -DCNXTSERIAL_INCLUDE_CORE <--- commented out 

   1. serial_hsf.o: serial_core.c serial_core.h <----commented out 

Again.. I iterate.. It might work without _any_ changes at all.. :) 

I suggest you to use the first version, since it's more easy.

Need the link for the driver?

[http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.18.00full/hsfmodem-7.18.00full.tar.gz](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.18.00full/hsfmodem-7.18.00full.tar.gz)


greetz

loko

---

### Post by loko on 2007-02-11
i can also lead you to these informations:

> Windows: Works fine, get the driver from Acer Europe.

FC4: Partial function - work in progress. It is a Conexant software controlled AC97 modem, so you will need the drivers from Linuxant. Good idea to check out linmodems.org as well for general background.

Unless there were major variations during the production run of the Aspire 3020 / 5020 machines, your modem should use a Conexant chipset. Use scanModem from linmodems.org to check. scanModem is pretty clever and will give you lots of useful information.

Find out what kernel and processor you have; for the Aspire 3023WLMi it's an i686.

]# uname -a

Go to linuxant.com and download the appropriate driver for your kernel, distro and processor.

I use Fedora Core 4, so got the rpm and installed it that way.

Check that the service hsf is running by starting it:

]# /sbin/service hsf start 

Then make sure the modules are loaded:

]# /sbin/lsmod

try:

]# /usr/sbin/hsfconfig

I get:

ERROR: no device detected by hsf driver

Ok, so you need to download the driver source (hsfmodem-7.18.00.05full-1.i386.rpm.zip), and the newdev patch (hsf-7.18.00.05-newdev.patch).
Note - future releases of hsfmodem will probably integrate this patch, so you may only have to install the plain RPM

Remove the previous version of the hsfmodem RPM (I use Synaptic). Extract and install the hsfmodem source RPM. Copy the patch to /usr/lib/hsfmodem. Patch the sources with

]# patch -p1 <hsf-7.18.00.05-newdev.patch

Compile the sources with

]# cd modules
]# make

Now run

]# /usr/sbin/hsfconfig

Which will prompt you to remove the current modules and to compile / install some new ones. Press enter, the defaults should be fine.

(While figuring this out, I also ran make install directly after make, so if you are having trouble, try that.)

After this, I had a working modem. I used Fedora's Network Configuration GUI to install a new device and enter my ISP's phone number details. This information is stored in /etc/wvdial.conf. Some of it is generic to the modem, some is specific to your ISP settings. You can double click on ppp0 to get the modem to initialise, just make sure that flow control is set to Software / XONXOFF. I am having trouble maintaining a connection, but at least I can hear the modem intialising and negotiating a connection with my ISP.

On the command line you initialise the modem like so

]# /sbin/ifup yourisp

Note, using Modem0, ppp0, /dev/modem as 'yourisp' does not work. You must use the Dialler ID from your /etc/wvdial.conf, as in, [Dialler yourisp].

]# /sbin/ifconfig
ppp0  Link encap:Point-to-Point Protocol
      inet addr:219.88.31.109  P-t-P:192.168.9.133  Mask:255.255.255.255
      UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
      RX packets:12 errors:1 dropped:0 overruns:0 frame:0
      TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:3
      RX bytes:210 (210.0 b)  TX bytes:228 (228.0 b)

]# ping 192.168.9.133
PING 192.168.9.133 (192.168.9.133) 56(84) bytes of data.
64 bytes from 192.168.9.133: icmp_seq=0 ttl=255 time=13549 ms
64 bytes from 192.168.9.133: icmp_seq=1 ttl=255 time=12613 ms
64 bytes from 192.168.9.133: icmp_seq=2 ttl=255 time=11718 ms

So there is a bit of a problem here but at least the computers are talking to each other, albeit at a level not much higher than morse code. I will look into this and publish any solutions here shortly

The support team at Linuxant suggested trying hsfconfig with a trial licence: This did not work for me at all, in fact it was worse than the unlicensed, crippled version of the driver. My computer locked up completely! I have tried compiling the driver with 4KSTACKS disabled in the kernel, to no avail.

NEWSFLASH One user has reported success with the modem on their Aspire 3023. I received this email:

25/11/2005 22:21
Hi, Michael!
 
I found the way how to make modem work under Linux so you can also try.
You must download new hsf modem driver from linuxant, but download souce code,
the name is hsfmodem-7.18.00.07full.tar.gz
After untaring and unziping put in the hsfmodem directory file that is in [B]
 [this attachment]("http://doube.net/files/hsfuniversalpatch-1.2.tar.gz") [/B] and run it in shell. (this is a litle bit of cheating, but it is working :-)  )
After that run make install, and after that hsfconfig.
Put in the licence informations that is written in this .dat file.
 
I use suse 9.3 and kpppd and my second init string must be AT&FW3+M5=V90
 
the init string that they suggest dos not work for me.
 
Speed is just 14 000, but I will try to make it faster.
 
Good Luck!

dejan kuticic

And a few days later, this email:

30/11/2005 22:48

Now I changed first init string in:AT &FW3+MS=V92,1,28800,33600,28800,56000
and second init string in:ATX3
 
and I have full 52000 speed. The line is not stable too much,
some times it disconnects but it is working, that is also something :)
 
Cheers!

I haven't tried these instructions yet, due to having neither time nor a dial-up account to test with. I can pass on any questions you might have for Dejan if you need further assistance.


hope it helps you

---

### Post by crazy___cow on 2007-02-15
I found a way to set max speed with the linuxant proprietary drivers.

[http://www.ubuntuforums.org/showthread.php?t=321063&highlight=linuxant](http://www.ubuntuforums.org/showthread.php?t=321063&highlight=linuxant)

---

### Post by loko on 2007-02-20
> **crazy___cow said:**
> I found a way to set max speed with the linuxant proprietary drivers.

[http://www.ubuntuforums.org/showthread.php?t=321063&highlight=linuxant](http://www.ubuntuforums.org/showthread.php?t=321063&highlight=linuxant)

your thread has been deleted by the forum-admins.

---

### Post by hokutonoken on 2007-02-27
Here is the definitive tutorial for installing Conexant free modules on Ubuntu


[http://www.ubuntuforums.org/showthread.php?t=190728](http://www.ubuntuforums.org/showthread.php?t=190728)

Hint: read the latest posts as they contain useful add-ons to original howto.

Please be warned:  free modules work only with Dapper. No one has ported modules to Ubuntu Edgy and later versions, yet. (as of February 2007)

---

### Post by term007 on 2007-03-06
> **loko said:**
> your thread has been deleted by the forum-admins.
 but google cashed this page for us
just type in google search this:
linuxant crazy___cow site:[http://ubuntuforums.org](http://ubuntuforums.org)
:)

---

