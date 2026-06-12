---
title: "Wi-fi adapter Intel 6205 does not work"
date: 2014-07-25
forum: Hardware
---

### Post by ivanovdw on 2014-07-25
Hi 2 all!
I have laptop Dell Xps 15 (L502x) with Intel card 1030. I decided to replace card on Intel 6205, cause wi-fi was tooooo slooooow.
I have two OS: Windows 7 and Linux (archlinux, kernel 3.15.5-2).
  In Windows card working without problems. But it’s not working in Linux
  Occurs error:
```


  [5.892574] IPv6: ADDRCONF (NETDEV_UP): enp6s0: link is not ready
[5.893096] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[5.893346] iwlwifi 0000:03:00.0: Radio type = 0x1-0x0-0x1
[6.898559] iwlwifi 0000:03:00.0: Failed to run INIT ucode: -110
[6.899882] iwlwifi 0000:03:00.0: Unable to initialize device.

```
Full log available  [here]("http://pastebin.com/wdnXvc5T"). I tried to boot from the live-usb Ubuntu. But there was the same error.
  Also, card visible by command «lspci».
  Then. I have another laptop with the same card Intel 6205  (but it's native). This laptop in Ubuntu works well.

It could be argued that the card does not work in Ubuntu because it is not native to laptop Dell Xps. But it’s works well in Windows.
 
 
  I tried to do:
- Google these theme
- install package intel-ucode
- underlay the firmware in /lib/firmware from the home site
- execute mkinitcpio-p Linux
- reinstall Linux package
- create the file /etc /modprobe.d/iwlwifi.conf containing
  ```

***options iwlwifi 11n_disable = 1***
***options iwlwifi swcrypto = 1***

```

   
  Nothing helped
  
What other actions I should try to do?
I am ready to go to ubuntu if the adapter will work in it.

---

### Post by jeremy31 on 2014-07-25
Run this in terminal and copy the url it returns
```
[COLOR=#2E8B57][FONT=Monaco]wget -N -t 5 -T 10 [/FONT][/COLOR]https://www.dropbox.com/s/jlohug6vfrr86lp/wireless_script2[COLOR=#2E8B57][FONT=Monaco] && chmod +x wireless_script2 && ./wireless_script2
```[/FONT][/COLOR]

---

### Post by ivanovdw on 2014-07-26
[result ubuntu 14.10](http://pastebin.com/muXBj9An)
[result ubuntu 14.04](http://pastebin.com/AcK0UexK)
[result archlinux]("http://pastebin.com/hGHFGtX0")

---

### Post by jeremy31 on 2014-07-26
Do you have the latest BIOS in your Dell?  It can be updated using windows

---

### Post by ivanovdw on 2014-07-26
I have the latest bios



L502XA12.exe                                             |                                             Windows/DOS                                             (10 MB)                                         

                                                                                                                                                                        Release date 10/26/2012 |                                             Last Updated 12/12/2013 |                                             Recommended 
                                                                                                                                                                                                                                                                                                            Version A12

---

### Post by jeremy31 on 2014-07-26
Since entering ```
**options iwlwifi 11n_disable = 1**options iwlwifi swcrypto = 1
```
Have you done a ```
sudo modprobe -rv iwlwifi
```and
```
sudo modprobe iwlwifi
```

or even ```
sudo modprobe -rv iwlwifi
```
```
sudo modprobe iwlwifi 11n_disable=1 swcrypto=1
```

---

### Post by ivanovdw on 2014-07-26
```

sudo modprobe -rv iwlwifi
sudo modprobe iwlwifi 11n_disable=1 swcrypto=1

```
dont help

dmesg
```

iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
iwlwifi 0000:03:00.0: Radio type = 0x1-0x0-0x1
iwlwifi 0000:03:00.0: Failed to run INIT ucode: -110 
iwlwifi 0000:03:00.0: Unable to initialize device.

```

---

### Post by varunendra on 2014-07-27
If it is NOT a UEFI based installation, try resetting the BIOS to factory defaults, then reboot and check if the errors persist. If they do, try the old power drain trick - Disconnect AC power, pull out the battery (even the one on the motherboard if that is easily accessible) > push the power button a few times to make sure any power remaining in the circuits is drained, leave it a couple of hours. Then reconnect everything and check if it starts playing well with Ubuntu. If still not, repeat the process, only leave it overnight instead of just a couple of hours - I remember some Dell laptops being reported here to need that long to completely reset.

I hope you were using default firmware in all those reports. To make double sure that those are correct ones, please post the outputs of -
```
uname -mr
sudo lshw -C network | grep iwlwifi
```

**@jeremy31,**
As far as I have seen, the "modprobe -rv iwlwifi" command fails in modern kernels to remove the driver with error message - "module is in use". To remove it, I have to remove the module "iwldvm" or "iwlmvm" - whichever is using it - first. So the entire sequence in newer kernel becomes -
```
sudo modprobe -rv iwldvm
sudo modprobe -v iwlwifi *<whatever parameters you want here>*
sudo modprobe -v iwldvm
```
Of course the "iwldvm" needs to be replaced with "iwlmvm" if that one is in use in the system. Removing iwldvm (or iwlmvm) automatically removes iwlwifi, so that is not needed to be removed separately. But to be extra sure, the first command can be changed to -
```
sudo modprobe -rv iwldvm iwlwifi[/I]
```
The only thing to remember is to remove those drivers first (or simultaneously) that may be using the module that you are trying to remove. Else modprobe -r will fail with "module is in use" error.

---

### Post by jeremy31 on 2014-07-27
> **varunendra said:**
> 
**@jeremy31,**
As far as I have seen, the "modprobe -rv iwlwifi" command fails in modern kernels to remove the driver with error message - "module is in use". To remove it, I have to remove the module "iwldvm" or "iwlmvm" - whichever is using it - first. So the entire sequence in newer kernel becomes -
```
sudo modprobe -rv iwldvm
sudo modprobe -v iwlwifi *<whatever parameters you want here>*
sudo modprobe -v iwldvm
```
Of course the "iwldvm" needs to be replaced with "iwlmvm" if that one is in use in the system. Removing iwldvm (or iwlmvm) automatically removes iwlwifi, so that is not needed to be removed separately. But to be extra sure, the first command can be changed to -
```
sudo modprobe -rv iwldvm iwlwifi[/I]
```
The only thing to remember is to remove those drivers first (or simultaneously) that may be using the module that you are trying to remove. Else modprobe -r will fail with "module is in use" error.

It seems my laptops have a /etc/modprobe.d/iwlwifi.conf file that removes the others along with iwlwifi.  The file exists on Ubuntu 14.04 and its derivatives even on the laptops I have that don't have intel wifi.  I am not sure what Ubuntu version it was first added as one machine I have with Linux Mint 13(Ubuntu 12.04) does not have this file

The file contains this
```
# /etc/modprobe.d/iwlwifi.conf# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
```

---

### Post by varunendra on 2014-07-27
That file and the separate microcode drivers (iwldvm and iwlmvm) were first included in Ubuntu 13.04. But the conf file (with exactly same contents as it currently has) didn't do what it was supposed to do (I noticed that file later, but noticed "iwldvm" much earlier when users started reporting the error while trying to remove iwlwifi directly).

However, I just tested it again on 14.04 live session, and now it seems to do the job properly. Perhaps it was some now-fixed bug in the underlying mechanism that relates modprobe commands with settings in modprobe.d directory. Still though, removing iwlwifi directly removes the iwl?vm file also - okay, but then reloading only iwlwifi, I believe, does only half the job. I don't have the hardware to test myself, but I believe loading the microcode driver is necessary to activate the card properly.

Now that we have started this discussion, I'll ask dr. chili555 to test if loading iwlwifi is enough to make it work, he has an Intel card to test and confirm that.

---

### Post by jeremy31 on 2014-07-27
> **varunendra said:**
> That file and the separate microcode drivers (iwldvm and iwlmvm) were first included in Ubuntu 13.04. But the conf file (with exactly same contents as it currently has) didn't do what it was supposed to do (I noticed that file later, but noticed "iwldvm" much earlier when users started reporting the error while trying to remove iwlwifi directly).

However, I just tested it again on 14.04 live session, and now it seems to do the job properly. Perhaps it was some now-fixed bug in the underlying mechanism that relates modprobe commands with settings in modprobe.d directory. Still though, removing iwlwifi directly removes the iwl?vm file also - okay, but then reloading only iwlwifi, I believe, does only half the job. I don't have the hardware to test myself, but I believe loading the microcode driver is necessary to activate the card properly.

Now that we have started this discussion, I'll ask dr. chili555 to test if loading iwlwifi is enough to make it work, he has an Intel card to test and confirm that.

I can confirm on Intel 7260 dual band, and Intel 6250

I actually thought it was one of your posts that recommended the use of modprobe over rmmod and insmod because modprobe took care of dependencies

---

### Post by varunendra on 2014-07-29
> **jeremy31 said:**
> I actually thought it was one of your posts that recommended the use of modprobe over rmmod and insmod because modprobe took care of dependencies

Yes I have recommended that several times on the forums. The 'elegancy' in the modprobe commands is that it returns an error if you try to remove a module that is being used by another module or a process which you don't have privilege to stop. Whereas with rmmod, you can 'force remove' a module with "-f" switch, even if that module is in use. At least that is what the man page says. Another thing is that when you remove a module with modprobe, it removes all the dependency modules as well if they are not required by other modules. The 'rmmod' command doesn't do this.

Anyway, regarding the "iwl?vm" confusion, were you able to connect after reloading just "iwlwifi"? My concerns were based on not just assumption, but this comment in the driver's [code]("http://lxr.free-electrons.com/source/drivers/net/wireless/iwlwifi/Kconfig") -
> "WARNING: iwlwifi is useless without IWLDVM or IWLMVM"

---

### Post by jeremy31 on 2014-07-29
It actually loaded iwl*vm along with cfg80211 and mac80211 depending on chipset/firmware. I tried the same modprobe commands on my dell with a 1030 and it worked except that it wouldn't connect until I rebooted, strange considering lsmod showed that everything loaded-dmesg showed the authenticating and deauthenticated by local choice 3.  I would swap cards in that machine with a 2200 or a 7260 if it didn't require the removal of so much stuff

---

### Post by varunendra on 2014-07-29
Yup, I got a reply PM from dr. chili555 last night, and he confirmed the same behaviour - iwl?vm was automagically loaded, but failed to connect until reboot. I am surprised at this unexpected behaviour of auto-loading of iwl?vm modules - working or not is a different issue.

As per my understanding, the .conf file does not and can not load the 'iwl?vm' module - it is only coded for removal of it. So perhaps it is some code in the iwlwifi driver itself that calls the required iwl?vm module - something similar to "ssb" or "bcma" mechanism that works with broadcom chips.

What I am surprised at is that I tried that same modprobe sequences (modprobe -v iwldvm > modprobe -rv iwlwifi > modprobe -v iwlwifi) myself on a 14.04 Live session on a VM here, and it FAILS to load iwl?vm module when running "modprobe -v iwlwifi" directly on it. So with confirmations from you and dr. chili, it seems that whether it will load with iwlwifi or not depends on whether a suitable Intel card is present or not in the system. It obviously wasn't in the VM.

---

