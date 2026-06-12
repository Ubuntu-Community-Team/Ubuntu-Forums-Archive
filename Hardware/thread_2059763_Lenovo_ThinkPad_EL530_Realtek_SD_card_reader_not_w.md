---
title: "Lenovo ThinkPad E/L530: Realtek SD card reader not working"
date: 2012-09-18
forum: Hardware
---

### Post by buzzcook on 2012-09-18
Here's the English translation of the [fix kindly provided by our Swiss colleague]("http://forum.ubuntuusers.de/topic/unbekannter-realtek-sd-kartenleser-einrichten-/") (in German) for an SD card reader that wasn't working on my ThinkPad L530 / his E530:

[LIST=1]
[*]Enter this command in the terminal:
lspci
The terminal returns the following output:
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)
[*]Head over to the [Realtek driver download site]("http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false#2").
[*]Download *PCIE RTS5229 card reader driver for Linux*.
[*]Unpack it twice e.g. to your /tmp folder.
The 2nd unpack produces a directory called "rts5229".
[*]Enter:
cd rts5229
[*]As described in the *README.tx*t file, enter these three commands (the last two must be as sudo):
make
sudo make install
sudo depmod
[*]Reboot your computer or alternatively enter this command to get the card reader working immediately (loads the kernel module rts5229):
sudo modprobe rts5229
[/LIST]
Hey presto!

---

### Post by musicpiano on 2012-12-05
This is extremely helpful . Thank you very very much . :p

---

### Post by okanagansage on 2013-01-20
I have the same card reader in my HP Pavilion g6-2090ca notebook. 

Thanks buzzcook for your post. I found it just after finding the Realtek driver webpage that you link to. I wanted to add a few things. 

The 'make' command wouldn't work for me with or without sudo in front. I had to use 'sudo su' first and then the 'make' command after. I also ran into another error which experienced people might find obvious but I had to search online for the answer. I'm gonna walkthrough what I did and it may help someone else. 

To find out what my card reader was (make, device id, etc) I tried lspci. It was listed but didn't say 'card reader' and I didn't know it's made by realtek. I guess I could have googled every device in the lspci output that I wasn't sure of but instead I went into Windows 7 device manager to look for it. I had to click on the item whose first word is memory (can't remember exactly) and the only item in the submenu was Realtek Card Reader. On a different computer of mine the card reader is under a different heading so you may have to look for it. Right click on it, choose properties (properties window pops up), click on the details tab, click on the drop-down menu and choose 'hardware id'. The ID  is a string of characters with 'VEN_10EC&DEV_5229' in the middle. I believe it also had rev_01 in that string of characters. 
In Ubuntu, using the command 'lspci -nn' shows the vendor/device number as "Realtek Semiconductor Co., Ltd. Device [10ec:5229] (rev 01)"
Using just lspci shows "Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)"

I googled 10ec:5229 and found the Realtek driver webpage that buzzcook links to (it was on the first page of results). On the realtek page it shows the card reader as "PCIE RTS5229 card reader". To make sure that is the exact same one I googled that and found this thread, which confirmed it for me. 

I downloaded the driver, extracted the zip file, then extracted the tar.bz2 file, opened the current folder as root (in the 'tools' menu of the file manager), copied and pasted the folder to my /tmp folder and then opened a terminal. 

Tried the make command:
```
paul@notebook-pc:/tmp/rts5229$ make
cp -f ./define.release ./define.h
cp: cannot create regular file `./define.h': Permission denied
make: *** [default] Error 1
```Tried sudo make:
```
paul@notebook-pc:/tmp/rts5229$ sudo make
[sudo] password for paul: 
cp -f ./define.release ./define.h
make -C /lib/modules/3.2.0-36-generic/build/ SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-36-generic'
/usr/src/linux-headers-3.2.0-36-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: 1: gcc: not found
make[3]: *** [scripts/basic/fixdep] Error 127
make[2]: *** [scripts_basic] Error 2
make[2]: *** No rule to make target `arch/x86/tools/relocs.c', needed by `arch/x86/tools/relocs'.  Stop.
make[1]: *** [archscripts] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-36-generic'
make: *** [default] Error 2
```Googled the 'stack protector' and 'gcc not found' errors. 
Installed gcc in Synaptic (probably could have done it with sudo apt-get install gcc).

Was still getting errors:
```
paul@notebook-pc:/tmp/rts5229$ sudo make
cp -f ./define.release ./define.h
make -C /lib/modules/3.2.0-36-generic/build/ SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-36-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf --silentoldconfig Kconfig
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-36-generic'
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-36-generic'
make[2]: *** No rule to make target `arch/x86/tools/relocs.c', needed by `arch/x86/tools/relocs'.  Stop.
make[1]: *** [archscripts] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-36-generic'
make: *** [default] Error 2
```Googled some more. Installed 'build-essential'. I'm not sure if this was necessary or not.
Was still getting an error when trying sudo make. 

Found this online:
> Beware of using sudo for the first command. I got this error until I realized my mistake.

$ sudo make
cp -f ./define.release ./define.h
make -C /lib/modules/3.2.0-31-generic/build/ SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-31-generic'
make[2]: *** No rule to make target `arch/x86/tools/relocs.c', needed by `arch/x86/tools/relocs'.  Stop.
make[1]: *** [archscripts] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-31-generic'
make: *** [default] Error 2Used 'sudo su' (press enter ), then 'make'. This time the make command worked for me. 
The rest is as explained in the read-me file and buzzcook's post:
```
root@notebook-pc:/tmp/rts5229# sudo make install
cp rts5229.ko /lib/modules/3.2.0-36-generic/kernel/drivers/scsi -f

root@notebook-pc:/tmp/rts5229# sudo depmod

root@notebook-pc:/tmp/rts5229# sudo modprobe rts5229
```I've installed drivers once or twice before but this is the first time using the modprobe command. I still primarily use Windows but am slowly learning more and more commands. I hope this helps someone.

---

### Post by denesb on 2013-04-01
In order to be able to compile the driver you have to have the linux-header package installed for your current kernel. It might be obvious, but it was not obvious for me and it took me half an hour to figure out why can't I compile the driver.

---

### Post by descomputer on 2013-05-06
Running Ubuntu 12.04 32bit on a Lenovo E535.
Followed the directions (which were absolutely accurate and very easy) and BAM - My Card Reader is Working.
Thank You Very Much!!

---

### Post by pushpsmarty on 2014-01-18
I have downloaded drivers from the same website as you suggested. But there are some errors while making driver. Errors are:

/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:266:2: error: unknown field &#8216;proc_info&#8217; specified in initializer
  .proc_info =   proc_info,
  ^
/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:266:2: warning: initialization from incompatible pointer type [enabled by default]
/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:266:2: warning: (near initialization for &#8216;rtsx_host_template.proc_dir&#8217;) [enabled by default]
/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:914:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtsx_probe&#8217;
 static int __devinit rtsx_probe(struct pci_dev *pci, const struct pci_device_id *pci_id)
                      ^
/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:1069:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtsx_remove&#8217;
 static void __devexit rtsx_remove(struct pci_dev *pci)
                       ^
/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:1094:11: error: &#8216;rtsx_probe&#8217; undeclared here (not in a function)
  .probe = rtsx_probe,
           ^
/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:1095:2: error: implicit declaration of function &#8216;__devexit_p&#8217; [-Werror=implicit-function-declaration]
  .remove = __devexit_p(rtsx_remove),
  ^
/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:1095:24: error: &#8216;rtsx_remove&#8217; undeclared here (not in a function)
  .remove = __devexit_p(rtsx_remove),
                        ^
/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:262:34: warning: &#8216;rtsx_host_template&#8217; defined but not used [-Wunused-variable]
 static struct scsi_host_template rtsx_host_template = {
                                  ^
/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:476:12: warning: &#8216;rtsx_control_thread&#8217; defined but not used [-Wunused-function]
 static int rtsx_control_thread(void * __dev)
            ^
/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:585:12: warning: &#8216;rtsx_polling_thread&#8217; defined but not used [-Wunused-function]
 static int rtsx_polling_thread(void * __dev)
            ^
/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:739:13: warning: &#8216;quiesce_and_remove_host&#8217; defined but not used [-Wunused-function]
 static void quiesce_and_remove_host(struct rtsx_dev *dev)
             ^
/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:775:13: warning: &#8216;release_everything&#8217; defined but not used [-Wunused-function]
 static void release_everything(struct rtsx_dev *dev)

/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:785:12: warning: &#8216;rtsx_scan_thread&#8217; defined but not used [-Wunused-function]
 static int rtsx_scan_thread(void * __dev)
            ^
/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:810:13: warning: &#8216;rtsx_init_options&#8217; defined but not used [-Wunused-function]
 static void rtsx_init_options(struct rtsx_chip *chip)
             ^
cc1: some warnings being treated as errors
make[2]: *** [/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.o] Error 1
make[1]: *** [_module_/home/pushpi/Realtek_RTS5229_Linux_Driver_v1.07/rts5229] Error 2
make: *** [default] Error 2

---

### Post by d-davek on 2014-01-24
Thanks** buzzcook**[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=872750"), this working perfect on HP Pavilion G6

---

### Post by fumblejack on 2014-04-27
I am getting the same error as pushpsmarty. This is through su. Someone please help!

---

### Post by davey3 on 2014-06-30
> **fumblejack said:**
> I am getting the same error as pushpsmarty. This is through su. Someone please help!

Same here.

EDIT: Just found a tip on this article: [http://abhinavgupta2812.wordpress.com/2014/01/28/getting-a-realtek-sd-card-reader-to-work-on-linux-tried-and-tested-on-debian/](http://abhinavgupta2812.wordpress.com/2014/01/28/getting-a-realtek-sd-card-reader-to-work-on-linux-tried-and-tested-on-debian/)
It suggests there's a weird thing happening with kernels above 3.6.x, so I removed all instances of [COLOR=#000000][FONT=Helvetica Neue]&#8220;__devinit&#8221; &#8220;__devexit&#8221; and &#8220;__devexit_p&#8221; from rtsx.c. This greatly shortened, although did not eliminate, my awful wall of errors. This is now the output:

[/FONT][/COLOR]/tmp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:266:2: error: unknown field &#8216;proc_info&#8217; specified in initializer
  .proc_info =   proc_info,
  ^
/tmp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:266:2: warning: initialization from incompatible pointer type [enabled by default]
/tmp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:266:2: warning: (near initialization for &#8216;rtsx_host_template.proc_dir&#8217;) [enabled by default]
make[2]: *** [/tmp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.o] Error 1
make[1]: *** [_module_/tmp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make: *** [default] Error 2

What now? What is this proc_info thing? Incompatible pointer type? What. What.

---

### Post by garic-simonov on 2014-07-18
> **davey3 said:**
> Same here.

EDIT: Just found a tip on this article: [http://abhinavgupta2812.wordpress.com/2014/01/28/getting-a-realtek-sd-card-reader-to-work-on-linux-tried-and-tested-on-debian/](http://abhinavgupta2812.wordpress.com/2014/01/28/getting-a-realtek-sd-card-reader-to-work-on-linux-tried-and-tested-on-debian/)
It suggests there's a weird thing happening with kernels above 3.6.x, so I removed all instances of [COLOR=#000000][FONT=Helvetica Neue]“__devinit” “__devexit” and “__devexit_p” from rtsx.c. This greatly shortened, although did not eliminate, my awful wall of errors. This is now the output:

[/FONT][/COLOR]/tmp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:266:2: error: unknown field ‘proc_info’ specified in initializer
  .proc_info =   proc_info,
  ^
/tmp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:266:2: warning: initialization from incompatible pointer type [enabled by default]
/tmp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.c:266:2: warning: (near initialization for ‘rtsx_host_template.proc_dir’) [enabled by default]
make[2]: *** [/tmp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229/rtsx.o] Error 1
make[1]: *** [_module_/tmp/Realtek_RTS5229_Linux_Driver_v1.07/rts5229] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make: *** [default] Error 2

What now? What is this proc_info thing? Incompatible pointer type? What. What.



I spent also hours in searching for a solution at the end I commented this line and.....it works!!!
So put two slashes in the beginning of this line in rtsx.c
Should be like that:
//    .proc_info =            proc_info,

Cheers!

---

