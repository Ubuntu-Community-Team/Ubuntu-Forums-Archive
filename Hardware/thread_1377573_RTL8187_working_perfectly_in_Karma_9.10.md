---
title: "RTL8187 working perfectly in Karma 9.10"
date: 2010-01-10
forum: Hardware
---

### Post by Virchanza on 2010-01-10
The RTL8187 driver that comes shipped with Ubuntu is broken, it causes the connection to drop out very frequently.

I installed Ubuntu Karma 9.10 to my hard disk just yesterday and I've spent all day today trying to get my wireless card working properly.

After hours of pulling my hair out, compiling and patching different drivers, I finally stumbled across the following solution. Now my wireless card is working pefectly :)

```

cd
mkdir THANK_CHRIST_FOR_THAT
cd THANK_CHRIST_FOR_THAT
wget http://virjacode.com/projects/beefup/dloads/rtl8187L_linux_26.1039.0104.2010.release.tar.gz
tar xf rtl8187L_linux_26.1039.0104.2010.release.tar.gz
cd rtl8187L_linux_26.1039.0104.2010.release
make
sudo make install

```

Reboot your computer after you do all that, then enjoy.

---

### Post by Virchanza on 2010-01-10
One more thing: You have to repeat those steps every time you update your kernel.

---

### Post by bedhead75 on 2010-01-11
I got the exact same driver version directly from Realtek and I've followed all those instructions, "make" and "sudo make install" followed by a reboot.  Now network manager doesn't even see my network anymore.  When I run "sudo ifconfig wlan1 up", I get "ERROR while getting interface flags: No such device" (I have another network card on wlan0, so for me, the rtl8187 device was wlan1).  When I check "lsmod", I don't see any rtl8187 driver listed at all, and my original rtl8187 is missing and can't be "modprobe"'d.  How did you get this working exactly?

---

### Post by bedhead75 on 2010-01-11
OK, I got the wireless adapter to show up in network manager and I realize the driver is now called r8187l instead of rtl8187.  MY network adpater was being assigned to a different wlan# than I had originally thought so I had to manually ifconfig wlan# up. Anyways the problem I'm having now is that my entire system freezes up the minute I try connecting to a network and I have to hard reboot.  I was connecting to an open network and watching the system logs, it freezes up at the DHCPREQUEST step.  This is always reproducible.  You are having absolutely no problems at all?

---

### Post by Virchanza on 2010-01-11
> 
I got the exact same driver version directly from Realtek
The link I provided is for a special one that hasn't been released publicly yet (or at least that's what I'm told), I found it over on the Aircrack forum. There's a chance that it's been altered in some way, and maybe it's those alterations that are making it work right for me.

Download the driver from the link I provided and give it a go, it's worth a shot.

If it still doesn't work after that, then run this command in a terminal:

```

lsusb

```and then look for the entry of your wireless card. Mine looks like this:

```

Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

```The important thing is the ID, which for me is 0bda:8187.

You see, there's two kinds of RTL8187, there's the L version and the B version. (I only learned this yesterday because I've been e-mailing the guy who worked on the RTL8187 driver for Linux).

 If you post the ID of your card, we can figure out which version you have.

As for how I got it working on my own machine, well I literally just followed the steps I posted in my original post in this thread.

Also, I upgraded my kernel yesterday so I had to run those steps a second time, and again I had no problems.

I'm using my Alfa AWUS036h in Ubuntu 9.10 right now to write this post, it's working absolutely fine.

---

### Post by bedhead75 on 2010-01-12
Hey, thanks for your reply.  I downloaded the driver from the link you posted earlier.  Initial inspection suggests it's the same one I got directly from Realtek as the release notes and readme files are identical.  I went as far as make, make install, and reboot in the first part of the instructions, but I didn't install the wpa_supplicant because I wanted to test it by connecting to just an open network first.  The same thing happened and the system froze up immediately after connecting.  I was monitoring the syslog and it seems to freeze up shortly after outputing "ipv6 duplicate address detected", which I've never seen before using an older rt73 chipset adapter.  I'm not sure if the ipv6 duplicate address is related the freeze though.  During the "make" compiling step, I also get a few warnings such as the following:

warning: cast from pointer to integer of different size

warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long unsigned int’

warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘size_t’


I'm not sure if you got this as well, but I do have the the build-essential package from synaptic installed.  I'm not sure if I'm still missing something for that step.

I'm also using the same exact Alfa adapter as you, with the same ID and all, with the latest Ubuntu 9.10 2.6.31-17-generic kernel.  Any further advice would be greatly appreciated.

---

### Post by Virchanza on 2010-01-12
I didn't get any of those compiler warnings. Here's what I get when I compile the driver that's hosted on Virjacode.com:

```

virchanza@virchanza-laptop:~/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187_core.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_93cx6.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_wx.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_rtl8225.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_rtl8225z2.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187_led.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_pm.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_dm.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_softmac.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_rx.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_tx.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_wx.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_module.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_crypt.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187l.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187l.mod.o
  LD [M]  /home/virchanza/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187l.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
virchanza@virchanza-laptop:~/THANK_JESUS_CHRIST_FOR_THAT/rtl8187L_linux_26.1039.0104.2010.release$ 

```My first thought would be that you're running a version of Ubuntu that was built for a different CPU architecture. Are you using Ubuntu 64-Bit by any chance?

Type the following at a terminal:

```

uname -a

```Here's the output I get:

```

Linux virchanza-laptop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 **i686** GNU/Linux
```Note that mine says i686. What does your say? Post the entire output.

One other thing... if you look at the compiler warnings and tell me which file and line number they're coming from, I can have a look through the code and see what could be causing those warnings.

---

### Post by bedhead75 on 2010-01-12
Here's the uname -a output

```
Linux home-desktop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux
```


Here's the compiler output:


```
bedhead75@home-desktop:~/Downloads/rtl8187L_linux_26.1039.0104.2010.release$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187_core.o
/home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_tx’:
/home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187_core.c:1376: warning: cast from pointer to integer of different size
/home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187_core.c: In function ‘rtl8187_usb_initendpoints’:
/home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187_core.c:1582: warning: cast from pointer to integer of different size
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_93cx6.o
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_wx.o
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_rtl8225.o
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_rtl8225z2.o
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187_led.o
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_pm.o
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_dm.o
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_softmac.o
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_rx.o
/home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_rx.c: In function ‘ieee80211_network_init’:
/home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_rx.c:1046: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long unsigned int’
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_tx.o
/home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_tx.c: In function ‘ieee80211_xmit’:
/home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_tx.c:426: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_wx.o
/home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_wx.c: In function ‘ieee80211_wx_set_gen_ie’:
/home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_wx.c:887: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘size_t’
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_module.o
/home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_module.c: In function ‘store_debug_level’:
/home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_module.c:271: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_crypt.o
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187l.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187l.mod.o
  LD [M]  /home/bedhead75/Downloads/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187l.ko
```

     I am using 64-bit Ubuntu.  I'm not sure where to get file and error line numbers.  Are they there in the above code?  Let me know.  Thanks.

---

### Post by lwfinger on 2010-01-12
Does using the package "linux-backports-modules-wireless" help? I'm told that it contains the 2.6.32 wireless drivers.

---

### Post by bedhead75 on 2010-01-12
Unfortunately it doesn't seem to make a difference.

---

### Post by Virchanza on 2010-01-12
You've got 64-Bit Ubuntu, so your C compiler is set to compile for 64-Bit. When your C compiler's running in 64-Bit mode, some of the intrinsic types (such as pointers and integers) will be wider in size (e.g. 64-Bit instead of 32-Bit)... this can cause problems if the code was not written portably.

Judging by the warnings you're getting from the compilation, it looks like the driver code was not written to be portable with 64-Bit.

What you want to do is try out a 32-Bit version. I was gonna suggest that you use your own computer to compile the driver for 32-Bit, but after doing some websearching it turns out that it's a tad complicated to get a 64-Bit machine to compile a 32-Bit executable.

So I've compiled the driver for 32-Bit on my own machine and copied it to my webserver. I've done the "make" command already, so you only have to do "make install". As follows:

```

cd
mkdir dog
cd dog
wget http://virjacode.com/projects/beefup/dloads/RTL8187L_compiled_for_32bit.tar.gz
tar xf RTL8187L_compiled_for_32bit.tar.gz
cd RTL8187L_compiled_for_32bit
**----- DON'T DO "MAKE", I'VE ALREADY DONE IT** -----
sudo make install

```Worth a try! Let me know how you get on.

---

### Post by bedhead75 on 2010-01-12
I tried out what you suggested and I really appreciate what you did.  Unfortunately it's still freezing the second it connects to an open network.  I still get errors running "sudo make install".  Here's the output:

```
bedhead75@home-desktop:~/Downloads/RTL8187L_compiled_for_32bit$ sudo make install
kernel/drivers/net/wireless/rtl818x/rtl8187.ko: kernel/net/mac80211/mac80211.ko kernel/drivers/leds/led-class.ko kernel/drivers/misc/eeprom/eeprom_93cx6.ko kernel/net/wireless/cfg80211.ko
kernel/drivers/net/wireless/rtl818x/rtl8187.ko: kernel/net/mac80211/mac80211.ko kernel/drivers/leds/led-class.ko kernel/drivers/misc/eeprom/eeprom_93cx6.ko kernel/net/wireless/cfg80211.ko
make[1]: Entering directory `/home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187'
make -C /lib/modules/2.6.31-17-generic/build M=/home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187 CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/r8187_core.o
/home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/r8187_core.c: In function ‘rtl8180_tx’:
/home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/r8187_core.c:1376: warning: cast from pointer to integer of different size
/home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/r8187_core.c: In function ‘rtl8187_usb_initendpoints’:
/home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/r8187_core.c:1582: warning: cast from pointer to integer of different size
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/r8180_93cx6.o
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/r8180_wx.o
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/r8180_rtl8225.o
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/r8180_rtl8225z2.o
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/r8187_led.o
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/r8180_pm.o
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/r8180_dm.o
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_softmac.o
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_rx.o
/home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_rx.c: In function ‘ieee80211_network_init’:
/home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_rx.c:1046: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long unsigned int’
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_tx.o
/home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_tx.c: In function ‘ieee80211_xmit’:
/home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_tx.c:426: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_wx.o
/home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_wx.c: In function ‘ieee80211_wx_set_gen_ie’:
/home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_wx.c:887: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘size_t’
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_module.o
/home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_module.c: In function ‘store_debug_level’:
/home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_module.c:271: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_crypt.o
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/../ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/r8187l.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/r8187l.mod.o
  LD [M]  /home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187/r8187l.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
install -p -m 644 r8187l.ko /lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless
depmod -a
make[1]: Leaving directory `/home/bedhead75/Downloads/RTL8187L_compiled_for_32bit/rtl8187'
```


If it works perfectly for your 32-bit system then it must be a 32-bit versus 64-bit issue because I think that's the only difference here.  It looks like we're on the verge of getting the rtl8187 driver problem finally fixed.  I did e-mail Realtek earlier about the 64-bit issue but I haven't heard a thing yet.  Any other suggestions?

---

### Post by Virchanza on 2010-01-13
Your computer is recompiling the driver in 64-Bit mode (which we don't want!). I was hoping it would just take the 32-Bit executable files I had already compiled and then just install them to your system. However the "make" program deleted my 32-Bit files and replaced them with freshly-compiled 64-Bit files.

I don't know much about the "make" program... so I did a little websearching on it. I saw that it has a command-line option called "--touch" which specifies that the files should ***not*** be re-compiled... but I couldn't get it to work right on my computer (odds are I don't understand what it's actually supposed to do).

Anyway, I had a look through all the Makefiles and I extracted the commands that are used to install the driver. These are the commands that get executed (as root):

```

rm -fr /lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless/rtl8187.ko
rm -fr /lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless/rtl818x/rtl8187.ko

cp ./RadioPower.sh /etc/acpi/events/

cd rtl8187

install -p -m 644 r8187l.ko /lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless

depmod -a

```So from the start again, it would be:

```

cd
mkdir dog
cd dog
wget http://virjacode.com/projects/beefup/dloads/RTL8187L_compiled_for_32bit.tar.gz
tar xf RTL8187L_compiled_for_32bit.tar.gz

cd RTL8187L_compiled_for_32bit

sudo rm -fr /lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless/rtl8187.ko
sudo rm -fr /lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless/rtl818x/rtl8187.ko

sudo cp ./RadioPower.sh /etc/acpi/events/

cd rtl8187

sudo install -p -m 644 r8187l.ko /lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless

sudo depmod -a

```Hopefully that will work :popcorn:  Keep me posted! I'm not sure if you need to reboot after doing that but I suggest you do it anyway.
[SIZE=3]
[COLOR=Red]P.S. Remember that you will have to unpack the 32-Bit files again because your computer has overwritten them with 64-Bit versions.[/COLOR][/SIZE]

---

### Post by bedhead75 on 2010-01-13
I did everything exactly as you said, and then rebooted.  Upon reboot the network manager doesn't "see" the device.  The command "lsmod" doesn't show that the driver is listed and "iwconfig" doesn't show a wlan# that corresponds to the network adapter.  Unplugging it and plugging it back in doesn't help.  Running "lsusb" does show that the device is connected though, with the proper make and ID number.   
       
     I wish Realtek would have released a driver that's portable with 64-bit.  It would really make my day to get this finally working!  Anything else you think we could try?

---

### Post by Virchanza on 2010-01-22
Hey man, go to this page:

[http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)

and then search for "kerner" (yes they misspelled "kernel')

You'll see the following:

> 
**Will not compile on kerner 2.6.31 or above**

     Follow the patching instructions at the top of this page then:

```

  wget [http://github.com/nopper/archpwn/raw/master/repo/lkm-skel/rtl8187-ng/rtl8187-ng-2.6.31.patch](http://github.com/nopper/archpwn/raw/master/repo/lkm-skel/rtl8187-ng/rtl8187-ng-2.6.31.patch)
 patch -Np1 -i rtl8187-ng-2.6.31.patch

```Then proceed with make/make install.


I'd say it's worth a try!

---

### Post by bedhead75 on 2010-01-22
Unfortunately I'm still getting errors during the "make" step even after the patch:

```
bedhead75@home-desktop:~/Downloads/rtl8187_linux_26.1010.0622.2006$ make
rm -f ieee80211/Module.symvers 2>/dev/null
rm -f ieee80211/Modules.symvers 2>/dev/null
make -C ieee80211 all
make[1]: Entering directory `/home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211'
make -C /lib/modules/2.6.31-17-generic/build M=/home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o
  CC [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_rx.o
/home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_rx.c: In function ‘ieee80211_monitor_rx_rtl7’:
/home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_rx.c:107: warning: cast from pointer to integer of different size
  CC [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_tx.o
  CC [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.o
  CC [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_module.o
  CC [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt.o
  CC [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211-rtl.o
  LD [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211-rtl.ko
  CC      /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_wep-rtl.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make[1]: Leaving directory `/home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/ieee80211'
chmod +x symvers
./symvers
make -C beta-8187 all
make[1]: Entering directory `/home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/beta-8187'
make -C /lib/modules/2.6.31-17-generic/build M=/home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/beta-8187 modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.o
In file included from /home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:65:
/home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187.h:47:27: error: asm/semaphore.h: No such file or directory
make[3]: *** [/home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.o] Error 1
make[2]: *** [_module_/home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/beta-8187] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/bedhead75/Downloads/rtl8187_linux_26.1010.0622.2006/beta-8187'
make: *** [all] Error 2
```

I'm not sure what the problem is.  Perhaps it is still a 32-bit versus 64-bit issue and the driver was not designed to be compiled in 64-bit Ubuntu?

---

### Post by Virchanza on 2010-01-22
Find the file called **r8187.h**, and look for the following lines of text inside it:

```

      #include <asm/io.h>
      #include <asm/semaphore.h>

```You have to replace those lines with:

```

      #include <linux/io.h>
      #include <linux/semaphore.h>

```Then try to recompile.

---

### Post by bedhead75 on 2010-01-22
I made the changes and it fixes the errors at the bottom when compiling.  I am still getting the "warning: cast from pointer to integer of different size" error.  After "make install", I notice that the wireless signal for all networks is MUCH weaker than compared to the original rtl8187 driver.  Connecting to an open network also causes a system freeze that requires a hard reboot.  Not sure what's going on!

---

### Post by ZING on 2010-02-12
I have the same stats and adapter as you and i did the same thing as you listed, it works and all but I cant connect to all the wireless connection... I am trying to connect to Belkin_N_Wireless##### and it's got 4 out of 5 bars but it will not connect... :| is it cuz of the N?


update, I did the same thing on another pc with fresh ubuntu 9.10 and i was able to connect at 54% but was unable to view any web pages??

---

### Post by lwfinger on 2010-02-12
Your problem may be the N router, but I doubt it. I have successfully connected to pre-N routers.

The inability to browse web pages sounds like a DNS or routing problem.

Can you ping 216.83.154.106?

How about ping [www.samba.org?](www.samba.org?)

If the first works but the second does not, it is a problem with DNS. If neither wouk, it may be a routing problem.

---

### Post by ZING on 2010-02-12
> **lwfinger said:**
> Your problem may be the N router, but I doubt it. I have successfully connected to pre-N routers.

The inability to browse web pages sounds like a DNS or routing problem.

Can you ping 216.83.154.106?

How about ping [www.samba.org?](www.samba.org?)

If the first works but the second does not, it is a problem with DNS. If neither wouk, it may be a routing problem.



how do I ping?

---

### Post by lwfinger on 2010-02-12
Check 'man ping'.

---

### Post by BOFH+ on 2010-02-13
> **Virchanza said:**
> After hours of pulling my hair out, compiling and patching different drivers, I finally stumbled across the following solution. Now my wireless card is working pefectly :)

Thanks for posting the patched driver!

BTW I've finally found a patch for kernel 2.6.32 here: [http://trac.aircrack-ng.org/attachment/ticket/650/rtl8187_2.6.32.patch](http://trac.aircrack-ng.org/attachment/ticket/650/rtl8187_2.6.32.patch)

---

### Post by bedhead75 on 2010-02-13
So has anyone other than the OP gotten the rtl8187 wireless drivers to work perfectly in 64-bit Ubuntu Karmic (2.6.31.X)?  I'm talking decent wireless signals and internet connectivity speeds for encrypted networks here.  If so, exactly which driver version and which patches did you use?  It seems there are various driver versions and patches out there and so far none seem to work for me.

---

### Post by scottsee on 2010-02-18
Hi, I followed the original thread owners directions to patch my RTL8187 driver before noticing this was for a 32bit version, not my 64bit.  I'm getting the same kernel panic when my network manager connects to my SSID forcing a reboot. Is there a way to revert back to the original RTL8187 drivers?  Thanks.

Scott

---

### Post by bedhead75 on 2010-02-18
I fixed it by reinstalling the kernel from synaptic.  

[http://ubuntuforums.org/showthread.php?t=1378431](http://ubuntuforums.org/showthread.php?t=1378431)

---

### Post by zapho on 2010-03-26
> **bedhead75 said:**
> So has anyone other than the OP gotten the rtl8187 wireless drivers to work perfectly in 64-bit Ubuntu Karmic (2.6.31.X)?  

Its been nearly awhile since someone posted here, just curious about how you're all getting on with the rtl8187 drivers?

I'm having troube with 32-bit Karmic still. The drivers shipped with karmic would let me connect to encrypted networks but would stop working after about 8kb of data was sent.

I tried the OP's drivers and they complied without a problem. I can detect networks now but I can't connect to them. Would anyone have any suggestions?

Are there any new drivers to try?

---

### Post by Dragoon666 on 2010-04-05
sorry but i still not get it, i have tried but it returns me the next error
```
make
```
```
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187_core.o
/home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187_core.c: In function ‘rtl8180_tx’:
/home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187_core.c:1376: warning: cast from pointer to integer of different size
/home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187_core.c: In function ‘rtl8187_usb_initendpoints’:
/home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187_core.c:1582: warning: cast from pointer to integer of different size
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_93cx6.o
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_wx.o
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_rtl8225.o
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_rtl8225z2.o
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187_led.o
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_pm.o
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8180_dm.o
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_softmac.o
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_rx.o
/home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_rx.c: In function ‘ieee80211_network_init’:
/home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_rx.c:1046: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long unsigned int’
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_tx.o
/home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_tx.c: In function ‘ieee80211_xmit’:
/home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_tx.c:426: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_wx.o
/home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_wx.c: In function ‘ieee80211_wx_set_gen_ie’:
/home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_wx.c:887: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘size_t’
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_module.o
/home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_module.c: In function ‘store_debug_level’:
/home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_module.c:271: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_crypt.o
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/../ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187l.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187l.mod.o
  LD [M]  /home/dragoon/Escritorio/rtl8187L_linux_26.1039.0104.2010.release/rtl8187/r8187l.ko
**make[1]: se sale del directorio `/usr/src/linux-headers-2.6.31-20-generic'**
```

sorry about the spanish

the light on the ALFA AWUS036H turns green when i reboot it but when it seems to connect turns my screen on a black one and i have to reboot (similar to the blue death screen of microsoft)

my kernel is

```
Linux DragoonMint 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
```

any help???  :(

---

### Post by promicin on 2010-04-13
it should be noted that the real alfa awus036h's problem with its driver is that when an ap with -70db+ is used, the connection is established but there is no throughput. It is addressed in detail here: [https://bugzilla.kernel.org/show_bug.cgi?id=14168#c41](https://bugzilla.kernel.org/show_bug.cgi?id=14168#c41) 

I have posted as Bilal Khan there.

I think all this patch does is address the compilation errors starting from 2.6.31 and improves the functionality of the aircrack-ng suite. Its good for hacking, but not for surfing.

The solution is still as always, use the patched r8187 driver from aircrack on any linux distro with a kernel < 2.6.30

---

### Post by kukubau on 2010-05-05
> **Virchanza said:**
> The RTL8187 driver that comes shipped with Ubuntu is broken, it causes the connection to drop out very frequently.

I installed Ubuntu Karma 9.10 to my hard disk just yesterday and I've spent all day today trying to get my wireless card working properly.

After hours of pulling my hair out, compiling and patching different drivers, I finally stumbled across the following solution. Now my wireless card is working pefectly :)

```

cd
mkdir THANK_CHRIST_FOR_THAT
cd THANK_CHRIST_FOR_THAT
wget http://virjacode.com/projects/beefup/dloads/rtl8187L_linux_26.1039.0104.2010.release.tar.gz
tar xf rtl8187L_linux_26.1039.0104.2010.release.tar.gz
cd rtl8187L_linux_26.1039.0104.2010.release
make
sudo make install

```Reboot your computer after you do all that, then enjoy.


The driver can be found on Alfa network's website. That in case the link you posted goes dead.

[http://www.alfa.com.tw/in/front/bin/ptlist.phtml?Category=105397](http://www.alfa.com.tw/in/front/bin/ptlist.phtml?Category=105397)

It is the Linux(2010.1.29)[]("javascript:AWUS036H_Linux_2010_1_29()") driver. 

Greets.

---

### Post by kukubau on 2010-05-05
Has anyone made this work???

I've tried the realtek drivers rtl8187_linux_26.1025.0328.2007 and the latest rtl8187L_linux_26.1039.0104.2010 and couldn't make it work. It won't authenticate.

---

### Post by kukubau on 2010-05-07
The driver that comes with Ubuntu Lucid is working great. No need to patch it.

One thing. In case you own an Alfa, don't keep it too close of the AP. It will break the connection.

Does anyone know how could one patch the already installed stock drivers? Is there a way to do this? I know how to patch them prior to compiling them, but I'd like to know if the stock drivers can be patched.

Greets.

---

### Post by lwfinger on 2010-05-07
The package you want is compat-wireless, which should be in linux-backports-modules for whatever version you have. Compat-wireless contains the latest wireless drivers from the wireless-testing kernel tree, which is currently holding the material that will be in kernel 2.6.35.

---

