---
title: "How can I disable my discrete graphics card?"
date: 2009-10-30
forum: Hardware
---

### Post by phrizek on 2009-10-30
Hello, I recently bought a new laptop, the ASUS UL80vt. Practically everything works in Ubuntu 9.10 out of the box. However, my laptop has switchable hybrid graphics, with an integrated intel card as well as a discrete nvidia card. The problem I'm having is that Ubuntu detects and enables both cards, which makes my laptop warmer and kills its battery life (~12 hours rated battery life, but I only get ~3.5 in Ubuntu). I'm totally fine with just having the intel graphics, so I'm trying to figure out how to disable my nvidia chip. Does anyone know how this can be done? If you need any relevant information, please let me know. I really want to fix this issue because aside from it, this machine is the closest thing to the most perfect linux ultraportable I know.

---

### Post by phrizek on 2009-10-30
Can anyone please help me? I just need to figure out how to disable my nvidia card.

Here are my results from lspci | grep VGA:

> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a74 (rev a2)


Thanks in advance.

---

### Post by phrizek on 2009-10-30
Someone suggested that I blacklist my device, but I can't figure out my module name from lsmod and lspci. Can someone take a look and identify my device? The card is an nvidia G210M.

lsmod:

> Module                  Size  Used by
isofs                  36424  1 
udf                    88136  0 
nls_iso8859_1           5280  1 
nls_cp437               6976  1 
crc_itu_t               2336  1 udf
vfat                   13184  1 
fat                    59832  1 vfat
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
arc4                    2144  2 
snd_mixer_oss          18976  1 snd_pcm_oss
ecb                     3296  2 
uvcvideo               65260  0 
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ath9k                 278176  0 
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
mac80211              210104  1 ath9k
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath                    10304  1 ath9k
asus_laptop            21092  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
psmouse                57124  0 
snd_timer              26992  2 snd_pcm,snd_seq
serio_raw               6596  0 
led_class               5256  2 ath9k,asus_laptop
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
atl1c                  36516  0 
lp                     11908  0 
parport                40528  2 ppdev,lp
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
cfg80211              109144  3 ath9k,mac80211,ath
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
x_tables               25832  1 ip_tables
fbcon                  41344  72 
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
usb_storage            65952  1 
i915                  246984  3 
drm                   193856  3 i915
i2c_algo_bit            7076  1 i915
intel_agp              32816  2 i915
video                  23612  1 i915
output                  3680  1 video


lspci:

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a74 (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be3 (rev a1)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)


---

### Post by milou on 2009-10-31
Hi phrizek this is miloofr again ;) ... After some thoughts, I think I told you stupid stuff unhopefully :( .. Since you have no nvidia drivers loaded, if this was the driver loading that wakes up the GC it should not be waken up. So far...
Other routes may be:
1) did you try to switch off the GC within 7 and then boot ubuntu?
2) did you try to use the hardware switch (I read somewhere that there was a button that allowed to manually swith the GC)? 
3) Ask Asus to add an option in the boot to switch off the card and pray they will do it
4) help and get help from linux community: see for ex. [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/312756](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/312756) , we can help by providing DSDT info etc...

BTW, if you bought anything from Amazon, could you add [there]("http://www.amazon.com/UL30vt/forum/Fx1978M98LGJ2GT/Tx3TJDDWOALGBIS/6/ref=cm_cd_NOREF?_encoding=UTF8&cdERR=defaultCred&cdItems=25&asin=B002Q8HK7K&cdSort=oldest#CustomerDiscussionsNRPB") something like:
"Mr ASUS, will you add a BIOS option which allow to switch on/off the G210M please ??? This is VERY important for linux users, since hot switch is not implemented neither in XWindow nor in nvidia drivers at present. Please do it, this is a really KEY feature for linux users to use this laptop !"
I personnaly cannot because I never bought from Amazon/USA, since I'm french !

---

### Post by phrizek on 2009-10-31
> **milou said:**
> Hi phrizek this is miloofr again ;) ... After some thoughts, I think I told you stupid stuff unhopefully :( .. Since you have no nvidia drivers loaded, if this was the driver loading that wakes up the GC it should not be waken up. So far...
Other routes may be:
1) did you try to switch off the GC within 7 and then boot ubuntu?
2) did you try to use the hardware switch (I read somewhere that there was a button that allowed to manually swith the GC)? 
3) Ask Asus to add an option in the boot to switch off the card and pray they will do it
4) help and get help from linux community: see for ex. [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/312756](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/312756) , we can help by providing DSDT info etc...

BTW, if you bought anything from Amazon, could you add [there]("http://www.amazon.com/UL30vt/forum/Fx1978M98LGJ2GT/Tx3TJDDWOALGBIS/6/ref=cm_cd_NOREF?_encoding=UTF8&cdERR=defaultCred&cdItems=25&asin=B002Q8HK7K&cdSort=oldest#CustomerDiscussionsNRPB") something like:
"Mr ASUS, will you add a BIOS option which allow to switch on/off the G210M please ??? This is VERY important for linux users, since hot switch is not implemented neither in XWindow nor in nvidia drivers at present. Please do it, this is a really KEY feature for linux users to use this laptop !"
I personnaly cannot because I never bought from Amazon/USA, since I'm french !

Hello again. Thank you milou for all your help with this issue. I will try all of those things you mentioned when I have some time, including sending ASUS a nice email about including support for switching cards in a future BIOS update. The bug report you linked to was a very informative read, and it seems like this issue is less trivial than I thought. I'm still confident that developers will come through eventually and make it work sometime in the future. I want to help them along by adding a DSDT.dsl of my machine to that thread, but I am unfamiliar with the procedure used to generate a DSDT.dsl file. Do you (or anyone else reading this thread) know how to do this?

Thanks!

---

### Post by xoen on 2009-11-09
> **phrizek said:**
> Hello, I recently bought a new laptop, the ASUS UL80vt.

I'm interested in buying an Asus UL30A or UL30VT, I have to decide if buy the second one, the reason why I'm confused is for the switchable graphic cards, I don't want to have an unused piece of hardware I can't use.

I know it's not a so common configuration, but **how switchable graphic cards are managed in general on other laptops?** (in GNU/Linux of course :p)

---

### Post by phrizek on 2009-11-09
As far as I know, switchable graphics are unsupported (for all laptops) in GNU/Linux due to issues in X and graphics drivers. If you read the bug report linked in milou's post, you'll see what I'm talking about. 

Even though switching graphics is still unsupported, the UL80vt is working great for me with Ubuntu. I seem to get about 4-5 hours of battery life out of it, and I'm starting to think that the low(er) battery life isn't due to the graphics cards being on, but poor power management in linux (as well as that brightness bug that I should get around to fixing). If you don't have any need for the graphics performance, get the laptop with the integrated graphics. If the UL30 has the same components as my UL80, it should work fantastic out of the box (save for the brightness hotkeys not working correctly).

---

### Post by avilella on 2009-11-09
If it is an ATI graphics card, you should be able to switch it off with this method:

[http://ubuntuforums.org/showpost.php?p=7933876&postcount=11](http://ubuntuforums.org/showpost.php?p=7933876&postcount=11)

If it is an nvidia graphics car, the switch off procedure changes from one vendor to another. Here is a page that describes it for the Sony Vaio Z series:

[http://www.basyskom.org/~eva/log_installation_vaio_z21vnx.html](http://www.basyskom.org/~eva/log_installation_vaio_z21vnx.html)

Can I ask you to report the hybrid graphics info for the UL80vt here:
> [http://bugs.launchpad.net/bugs/312756](http://bugs.launchpad.net/bugs/312756)

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:
sudo apt-get install acpidump iasl
You can check the model and generation of you laptop with this command:
sudo dmidecode -s system-product-name

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug report. This information will allow the developers to fully implement the hybrid
graphics features for Linux.


> **phrizek said:**
> As far as I know, switchable graphics are unsupported (for all laptops) in GNU/Linux due to issues in X and graphics drivers. If you read the bug report linked in milou's post, you'll see what I'm talking about. 

Even though switching graphics is still unsupported, the UL80vt is working great for me with Ubuntu. I seem to get about 4-5 hours of battery life out of it, and I'm starting to think that the low(er) battery life isn't due to the graphics cards being on, but poor power management in linux (as well as that brightness bug that I should get around to fixing). If you don't have any need for the graphics performance, get the laptop with the integrated graphics. If the UL30 has the same components as my UL80, it should work fantastic out of the box (save for the brightness hotkeys not working correctly).

---

### Post by xoen on 2009-11-09
> **phrizek said:**
> As far as I know, switchable graphics are unsupported (for all laptops) in GNU/Linux due to issues in X and graphics drivers. If you read the bug report linked in milou's post, you'll see what I'm talking about. 
Thank you.

A question: It's possible choose/disable a graphic card from BIOS? At reboot XOrg starts without problems?

---

### Post by phrizek on 2009-11-09
> **xoen said:**
> Thank you.

A question: It's possible choose/disable a graphic card from BIOS? At reboot XOrg starts without problems?

You can't disable it in the BIOS :(

---

### Post by phrizek on 2009-11-09
> **avilella said:**
> If it is an ATI graphics card, you should be able to switch it off with this method:

[http://ubuntuforums.org/showpost.php?p=7933876&postcount=11](http://ubuntuforums.org/showpost.php?p=7933876&postcount=11)

If it is an nvidia graphics car, the switch off procedure changes from one vendor to another. Here is a page that describes it for the Sony Vaio Z series:

[http://www.basyskom.org/~eva/log_installation_vaio_z21vnx.html](http://www.basyskom.org/~eva/log_installation_vaio_z21vnx.html)

Can I ask you to report the hybrid graphics info for the UL80vt here:

Thank you! I've been trying to figure out how to get a dsdt file for days!

---

### Post by xoen on 2009-11-10
> **phrizek said:**
> You can't disable it in the BIOS :(
Wow, this means (99.9%) I will choose the "vanilla" UL30A with Intel X4500MHD, thank you for the response :).
BTW *the fact there is no option in BIOS sucks*.

---

### Post by szelek on 2009-11-24
My friend installed ubuntu 9.10 on his ASUS UL80 and there are problems with wifi. It keeps disconnecting every ~3 minutes. And battery life is realy poor in comparison to windows, it stays up for about 3 - 4 hours. So it sucks pretty much.

---

### Post by avilella on 2009-11-24
Any ideas what the battery life issue could be? Is there an option to switch off the nvidia card and only use the integrated intel chipset?

> **szelek said:**
> My friend installed ubuntu 9.10 on his ASUS UL80 and there are problems with wifi. It keeps disconnecting every ~3 minutes. And battery life is realy poor in comparison to windows, it stays up for about 3 - 4 hours. So it sucks pretty much.

---

### Post by Chareos on 2009-12-03
Would be possible (would someone be able) to write a script that makes the switch ?

1 - change xorg.conf videocard to use
2 - notify (ubuntu-notification) user that "next login will make use of XXX videocard"
2 - at next xorg startup, power off the discrete videocard if the integrated is used

For the point 2 : would be possible to power off the card using the same mechanism issued by the suspend system ?


If this is possible... well, we could get reasonably good features, and a mere re-logon is quite acceptable...

(I'm thinking to buy an UL30VT...)

---

### Post by bridgetbruston on 2009-12-03
You may be able to go into device manager (right click my computer and click properties then hit the hardware tab then click device manager) and under the "display" section, right click and select "disable" for the onboard video.

---

### Post by avilella on 2009-12-04
For those considering an Asus UL80Vt or UL30Vt, even if the BIOS doesn't specify an option to switch on/off the discrete graphics card, there is still an alternative in Linux, which is to use grub2-efi. It's been done for other linux hybrid graphics laptops (e.g. apple macbooks, sony vaio z-series, etc.) and it's in active development.

[http://grub.enbug.org/TestingOnEFI](http://grub.enbug.org/TestingOnEFI)
[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

There are several Linux users investigating with these kind of laptops, so it is reasonable to expect this feature to appear soon for Asus UL30/UL80 laptops.

> **Chareos said:**
> Would be possible (would someone be able) to write a script that makes the switch ?

1 - change xorg.conf videocard to use
2 - notify (ubuntu-notification) user that "next login will make use of XXX videocard"
2 - at next xorg startup, power off the discrete videocard if the integrated is used

For the point 2 : would be possible to power off the card using the same mechanism issued by the suspend system ?


If this is possible... well, we could get reasonably good features, and a mere re-logon is quite acceptable...

(I'm thinking to buy an UL30VT...)

---

### Post by fungi on 2009-12-05
Has anyone opened it up and seen if you can physically disable the nvidia card (ie remove a daughter board)?

Thinking of buying ul30vt or ul80vt, are there any other issues? does multi touch work? can you overclock it in Linux?

---

### Post by fungi on 2009-12-06
OK i've ordered the ul30vt.
See now that it comes with splashtop (express gate linux). Could somebody test the battery life under express gate and see what kind of battery performance that delivers?
If splashtop is disabling the nvidia graphics chip it may hold clues as to how we can disable it in ubuntu.

---

### Post by dj_aleks on 2009-12-07
Damn! I´ve also ordered a VT but i´m getting more and more uncertain the more i read about the graphics problems!
I really think the Nvidia card is a better choice, but i´d love the possibilituy to choose between that one and the Intelcard when i´m not doing any graphic intensive tasks....
I´m a photographer so i think i´d get more from the lappy with the Nvidia card..
What should i do!? =(

---

### Post by avilella on 2009-12-07
A question for phrizek and other Asus UL80Vt users:

Have you guys investigated if the nvidia graphics card can be switched off by other means?

All forum posts seem to indicate it's not possible through the BIOS,
but has anyone tried any other methods?

For example, it would great if you could post a DSDT table here:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756)

To compile your DSDT information, install if you haven't already the
acpidump and iasl tools:
sudo apt-get install acpidump iasl
You can check the model and generation of you laptop with this command:
sudo dmidecode -s system-product-name

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug
report. This information will allow the developers to fully implement
the hybrid graphics features for Linux.

> **dj_aleks said:**
> Damn! I´ve also ordered a VT but i´m getting more and more uncertain the more i read about the graphics problems!
I really think the Nvidia card is a better choice, but i´d love the possibilituy to choose between that one and the Intelcard when i´m not doing any graphic intensive tasks....
I´m a photographer so i think i´d get more from the lappy with the Nvidia card..
What should i do!? =(

The Sony Vaio SZ-series laptops have had a manual switch, and this is 3-4 years ago. The newer Vaio Z-series laptops also have the switch, but in Linux this is a special feature that needs to call a method in the BIOS. The DSDT table contains that method, but it took a bit of investigation to find out how.

So please submit your DSDT table as soon as possible so that we can find out what is the BIOS call for it.

---

### Post by dj_aleks on 2009-12-07
> **avilella said:**
> A question for phrizek and other Asus UL80Vt users:

Have you guys investigated if the nvidia graphics card can be switched off by other means?

All forum posts seem to indicate it's not possible through the BIOS,
but has anyone tried any other methods?

For example, it would great if you could post a DSDT table here:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756)

To compile your DSDT information, install if you haven't already the
acpidump and iasl tools:
sudo apt-get install acpidump iasl
You can check the model and generation of you laptop with this command:
sudo dmidecode -s system-product-name

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug
report. This information will allow the developers to fully implement
the hybrid graphics features for Linux.



The Sony Vaio SZ-series laptops have had a manual switch, and this is 3-4 years ago. The newer Vaio Z-series laptops also have the switch, but in Linux this is a special feature that needs to call a method in the BIOS. The DSDT table contains that method, but it took a bit of investigation to find out how.

So please submit your DSDT table as soon as possible so that we can find out what is the BIOS call for it.

What exactly IS a DSDT table?? haven't really got the hang of it?

---

### Post by avilella on 2009-12-07
DSDT table contains information about the ACPI features of the hardware. DSDT is an acronym for Differentiated System Description Table. This table contains the Differentiated Definition Block, which supplies the information and configuration information about the base system. It is always inserted into the ACPI Namespace by the OS at boot time. Unfortunately, many hardware vendors and OEMs are not capable of supplying fully functional tables. For details, see the ACPI specification, chapter 2.1 ([www.acpi.info](www.acpi.info)).

---

### Post by dj_aleks on 2009-12-07
> **avilella said:**
> DSDT table contains information about the ACPI features of the hardware. DSDT is an acronym for Differentiated System Description Table. This table contains the Differentiated Definition Block, which supplies the information and configuration information about the base system. It is always inserted into the ACPI Namespace by the OS at boot time. Unfortunately, many hardware vendors and OEMs are not capable of supplying fully functional tables. For details, see the ACPI specification, chapter 2.1 ([www.acpi.info](www.acpi.info)).

Okey, Will do as soon as i get the lappy! i really don't want to use Win just because of the GPU =/

---

### Post by ceolwulf on 2009-12-07
Kind of a bump for the thread but I too am getting an Asus UL30Vt-X1 and am going to run an incarnation of Ubuntu on it so any progress on this is extremely appreciated!

I suppose this is a little related but does anyone know if the CPU is overclocked in Linux or can this be edited in the BIOS? I'd love to have at least some control over the "Turbo33" since I won't really need it most of the time but would love to use it when I do.

Thanks!

---

### Post by dj_aleks on 2009-12-08
Btw, just read that the onboard nVidiacard on the 30VT actually is CUDA compatible :D

---

### Post by avilella on 2009-12-08
Yes, not only that but people has already successfully installed the CUDA/OpenCL drivers for Linux and used it to compile real code on it.

See here:

[http://linux-hybrid-graphics.blogspot.com/2009/12/how-to-use-nvidia-cudaopencl-linux-sdk.html](http://linux-hybrid-graphics.blogspot.com/2009/12/how-to-use-nvidia-cudaopencl-linux-sdk.html)

The graphics card in the Asus UL80Vt or UL30Vt is a new and powerful piece of compute! 

> **dj_aleks said:**
> Btw, just read that the onboard nVidiacard on the 30VT actually is CUDA compatible :D

---

### Post by dj_aleks on 2009-12-08
> **avilella said:**
> Yes, not only that but people has already successfully installed the CUDA/OpenCL drivers for Linux and used it to compile real code on it.

See here:

[http://linux-hybrid-graphics.blogspot.com/2009/12/how-to-use-nvidia-cudaopencl-linux-sdk.html](http://linux-hybrid-graphics.blogspot.com/2009/12/how-to-use-nvidia-cudaopencl-linux-sdk.html)

The graphics card in the Asus UL80Vt or UL30Vt is a new and powerful piece of compute!

Impressive indeed! Now if we just could get the graphics switching to work well, then this seems to be the best bang for the buck in terms of light and powerful laptops!

---

### Post by avilella on 2009-12-28
One of the Linux users has found a solution to switch off the nvidia card in the UL30Vt models, which by the looks of the DSDT tables, will also work for the UL50Vt and UL80Vt models with nvidia card.

It uses the ACPI P0P1.VGA._OFF method, which is the same for all 3 models.

The code file, "asus_nvidia.c" is derived from "lenovo_acpi.c" by Sylvain Joyeux.

Here is the original post and another one that adds hibernation support:
[http://forum.notebookreview.com/show...postcount=1239](http://forum.notebookreview.com/show...postcount=1239)
[http://forum.notebookreview.com/show...postcount=1244](http://forum.notebookreview.com/show...postcount=1244)

asus_nvidia.c
================================================== ======
#include <acpi/acpi.h>
#include <linux/suspend.h>

MODULE_LICENSE("GPL");

static acpi_handle root_handle;

static int kill_nvidia(void)
{
acpi_status status;
// The device handle
acpi_handle handle;
struct acpi_object_list args;
// For the return value
struct acpi_buffer buffer = { ACPI_ALLOCATE_BUFFER, NULL };

status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P1.VGA._OFF", &handle);
if (ACPI_FAILURE(status))
{
printk("%s: cannot get ACPI handle: %s\n", __func__, acpi_format_exception(status));
return -ENOSYS;
}

args.count = 0;
args.pointer = NULL;

status = acpi_evaluate_object(handle, NULL, &args, &buffer);
if (ACPI_FAILURE(status))
{
printk("%s: _OFF method call failed: %s\n", __func__, acpi_format_exception(status));
return -ENOSYS;
}
kfree(buffer.pointer);

printk("%s: disabled the discrete graphics card\n",__func__);
return 0;
}

static int power_event(struct notifier_block *this, unsigned long event,
void *ptr)
{
switch (event) {
case PM_POST_HIBERNATION:
kill_nvidia();
return NOTIFY_DONE;
case PM_POST_SUSPEND:
case PM_HIBERNATION_PREPARE:
case PM_SUSPEND_PREPARE:
default:
return NOTIFY_DONE;
}
}

static struct notifier_block power_notifier = {
.notifier_call = power_event,
};

static int __init asus_nvidia(void)
{
int ret = register_pm_notifier(&power_notifier);
if (ret) return ret;
return kill_nvidia();
}

static void dummy(void)
{
}

module_init(asus_nvidia);
module_exit(dummy);
================================================== ======

Makefile
================================================== ======
ifneq ($(KERNELRELEASE),)
obj-m := asus_nvidia.o
else
KERNELDIR ?= /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)

default:
$(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) modules

clean:
$(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) clean

endif
================================================== ======

To compile it, simply run:

Code:

make

To install it, run as root:
Code:

cp asus_nvidia.ko /lib/modules/`uname -r`/kernel/
depmod

To try it out, run as root:
Code:

modprobe asus_nvidia

To load it on each reboot on Ubuntu, run as root:
Code:

echo asus_nvidia >>/etc/modules

That last step will be different on other distros, e.g., on Gentoo you need to append the module name to /etc/modules.autoload.d/kernel-2.6.

---

### Post by blackmoon105 on 2010-01-04
Info about a .deb package on this post:[ http://ubuntuforums.org/showpost.php?p=8607972&postcount=5]("http://ubuntuforums.org/showpost.php?p=8607972&postcount=5")

---

