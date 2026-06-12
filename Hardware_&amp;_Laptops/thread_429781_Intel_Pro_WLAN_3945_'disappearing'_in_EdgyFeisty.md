---
title: "Intel Pro WLAN 3945 'disappearing' in Edgy/Feisty"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by Fogge on 2007-05-01
Hi, pretty new Ubuntuist here. I've ran 6.06 on my Dell Inspiron 640m laptop since january, decided to try Beryl in february and upgraded to 6.10 for that. After a few days lots of hardware functions ceased functioning (such as Function button + down/up arrows to adjust light intensity from the monitor, hardware buttons for volume control, and my wireless network card disappeared). I figured its not worth losing wireless capability to play around some and installed Windows via restoration disc and then wiped it for Ubuntu 6.06. Everythings been working just fine up until I upgraded to first 6.10, then immideatly to 7.04.

I've been using the laptop out of town, and sometimes when i get back home i need to remind the laptop to connect to the right network so my mom can surf on the laptop when im at home by my stationary computer.

This sunday, however, the laptop was working fine all weekend, i even had a small wifi network set up between my laptop and my Nintendo DS at the train home. I shut down the computer when the train stopped, took a bus home and my mom borrowed the laptop at once. She complained that "internet doesnt work" so i figured it was the same problem as before, and took the laptop to change the location to "Home".

I went System -> Administration -> Network, and my wireless card *was not in the list*, the regular network card and the built-in phone modem was, however. Neither did it turn up in the graphical System -> Preferences -> Hardware information list.

sudo lspci -v gives me a listing of hardware stuff and at the very bottom, "Network controller: Intel Corporation PRO/Wireless 3945ABG network connection (Rev: 02)" (and some more information, nothing really useful). This does NOT show up in the graphical interface.

/etc/network/interfaces states that the computer should look for SSID "LiU" when connecting wireless, LiU is the name of the network i used this weekend when i was out of town.

Does anyone have a clue as to what might be wrong, and how i could fix it?:(

---

### Post by Fogge on 2007-05-06
Bump (May an admin strike me down if it is too fast)

---

### Post by Fogge on 2007-05-09
Issue resolved thanks to chili555:

[email]wweston888 @hotmail.com[/email] says:
This is chili555 from the ubuntu forum. r u ready to fix ur wireless?
Fogge says:
i sure hope so.  
[email]wweston888 @hotmail.com[/email] says:
you have the laptop going next to you?
Fogge says:
in my lap.  
[email]wweston888 @hotmail.com[/email] says:
r u dual booting so u have to switch over?
Fogge says:
Nopers, this is my stationary computer
[email]wweston888 @hotmail.com[/email] says:
this may sound basic, but lets try
[email]wweston888 @hotmail.com[/email] says:
open a terminal and type sudo modprobe ipw3945
Fogge says:
type in my password and nothing happens
[email]wweston888 @hotmail.com[/email] says:
good!
[email]wweston888 @hotmail.com[/email] says:
now iwconfig
[email]wweston888 @hotmail.com[/email] says:
does eth1 show up?
Fogge says:
nopers
[email]wweston888 @hotmail.com[/email] says:
rats
[email]wweston888 @hotmail.com[/email] says:
is there a switch to turn off the wireless? did it get nudged off?
Fogge says:
there is no such switch
[email]wweston888 @hotmail.com[/email] says:
in iwconfig, all interfaces are 'no wireless extensions'?
Fogge says:
yup
Fogge says:
lo and eth0
[email]wweston888 @hotmail.com[/email] says:
rats....
[email]wweston888 @hotmail.com[/email] says:
when u do    sudo lshw -C network does it say 'off' or 'disabled'?
Fogge says:
neither
Fogge says:
it finds the Network controller and ID's it as the Intel Pro Wireless 3945ABG Network connection
[email]wweston888 @hotmail.com[/email] says:
try sudo ifconfig eth1 up and let me see the output
Fogge says:
eth1: ERROR while getting interface flags: No such device
[email]wweston888 @hotmail.com[/email] says:
rats squared....
[email]wweston888 @hotmail.com[/email] says:
take a look at dmesg | grep 3945 and see if there are any warnings or errors
Fogge says:
will our progress be hindered in any way if i hook up the wired network card to paste stuff in the pastebin for you?
[email]wweston888 @hotmail.com[/email] says:
nope
[email]wweston888 @hotmail.com[/email] says:
but remember to unhook and sudo ifdown eth0 when done
Fogge says:
[http://paste.ubuntu-nl.org/20078/](http://paste.ubuntu-nl.org/20078/)
[email]wweston888 @hotmail.com[/email] says:
Radio Frequency Kill Switch is On:
[email]wweston888 @hotmail.com[/email] says:
thats the key
[email]wweston888 @hotmail.com[/email] says:
jus sec, i may have the fix
Fogge says:
cool
Fogge says:
hmm, my computer is now showing signs of the exact same stuff that happened under 6.10 as well, the Fn+up/down arrows do NOT adjust the screen brightness
Fogge says:
dunno if it could do that earlier today or when that function also disappeared
[email]wweston888 @hotmail.com[/email] says:
 echo 0 | sudo tee /sys/bus/pci/drivers/ipw3945/*/rf_kill
[email]wweston888 @hotmail.com[/email] says:
then cat   /sys/bus/pci/drivers/ipw3945/*/rf_kill
[email]wweston888 @hotmail.com[/email] says:
see if 0 comes back
[email]wweston888 @hotmail.com[/email] says:
i wonder if, when Windows was on this lappy, Fn+F2 turned wireless on/off?
[email]wweston888 @hotmail.com[/email] says:
and thats wonky now, too?
Fogge says:
the first one prints a zero in the terminal and gives me a new command line, the second one says "resource temporarily unavailable"
[email]wweston888 @hotmail.com[/email] says:
now iwconfig, eth1 there?
Fogge says:
fn+f2 has been used to activate/deactivate the wireless in 6.06 and XP, yes
Fogge says:
nope
Fogge says:
but fn+f2 never made the interface disappear from the Sys -> Adm -> Network list
[email]wweston888 @hotmail.com[/email] says:
it sounds as if Ubuntu is not recognizing the special keys, in my IBM, there are a couple of packages u install to get all this to work
Fogge says:
but it recognized it earlier
Fogge says:
thats what so freaked out
Fogge says:
first the wireless goes out, now this
Fogge says:
EXACTLY like in 6.10
[email]wweston888 @hotmail.com[/email] says:
all this deteriorated in 6.10? and then u installed 7.04? izzat right?
Fogge says:
no, loong ago, i tried 6.10 just to try Beryl out
Fogge says:
things got farked, went back to 6.06
Fogge says:
7.04 gets out, i upgrade, install beryl, bang, my wireless farks out.
[email]wweston888 @hotmail.com[/email] says:
i found Beryl slowed stuff up, i uninstalled it!
Fogge says:
it is unistalled now
[email]wweston888 @hotmail.com[/email] says:
i am outa suggestions
[email]wweston888 @hotmail.com[/email] says:
sorry
[email]wweston888 @hotmail.com[/email] says:
rf_kill is crucial
Fogge says:
thats OK, i at least got to try some stuff that i havent seen before
[email]wweston888 @hotmail.com[/email] says:
search google for your laptop model and rf_kill
[email]wweston888 @hotmail.com[/email] says:
what model is it BTW?
Fogge says:
Dell Inspiron 640m
[email]wweston888 @hotmail.com[/email] says:
i would google this, too Max thermal spin reached
[email]wweston888 @hotmail.com[/email] says:
im not crazy about that
Fogge says:
ok, call me crazy but the wifi led is blinking like mad
Fogge says:
i DONT think it did that before
Fogge says:
holy ****
Fogge says:
the wireless interface is back
Fogge says:
i dont know what the hell we just did, but a reboot made it happen for real
Fogge says:
and i can now, after changing to correct SSID and entering WEP key access the internet...

Hope this could help someone else! (although i blame Beryl)

---

### Post by HuskyDev on 2007-05-11
I have the same exact problem on my Dell e1405's Intel/PRO 3945ABG wireless card.

When I initially installed Ubuntu 7.04 the wifi LED would flicker a lot, similar to what you described just before you magically got your wireless to work again.  This was only when I wasn't connected to a network.  When I was, the LED would go solid.

Then I discovered the "Desktop Effects" preference option, which I found out was the Beryl effects suite and decided to turn on.  I'm pretty sure after that point all indication of my wireless card disappeared.  The default restricted drivers that come with Feisty were still installed, but when popping up the GUI for "Restricted Drivers" in the administration tab, it says the drivers are "unused", where before it would say "in use".  Neither `ifconfig` nor `iwconfig` show my wireless interface (was eth1).

After following your post I thought that maybe turning off Beryl and restarting might help me too.  Unfortunately it didn't.  The fact that the card was recognized and usable before makes me doubt that I need some special module to reverse this effect.

I may try to reinstall the OS (trying Feisty again and going backward if necessary).  If anyone finds out anything new in the meantime, please let me know.

---

### Post by HuskyDev on 2007-05-11
An update:

I went through the above conversation and tried out all the commands that were used.  Shortly after running `sudo lshw -C network` my blinking wifi LED came back on, and magically everything went back to the way it was before.

Now I can actually work on getting the wireless to work properly...maybe even with WPA. =)

In conclusion, this result may have come from one or both of:

- turning off Beryl (in Feisty, turning off the "Desktop Effect" option in the preferences tab)
- running `sudo lshw -C network`

Anyone know what that command does?  I should hit up its manpage.

---

### Post by HuskyDev on 2007-05-16
Another update:

My previous solution appeared to be quite temporary.  After only an hour or so my wireless card disappeared off of cyberspace once again.

Anyway, as seems a common thing to do with Linux, I did a reinstall of the OS.  Magically, Beryl and wifi started working flawlessly...simultaneously in fact!

Not only that, but WPA started working for me as well, which was the next thing on my list to tackle.

It's magic.  The ghost code was at work.

-Kris

FYI:  I'm running Feisty on a Dell Inspiron e1405 with this wireless card.

---

### Post by emparq on 2007-05-23
I have a similar problem- eth1 disappearing on me. Though after observing the problem a few times, I noticed that it wasn't eth1 disappearing, but eth0, and as a result, eth1 would get bumped down to eth0. This behavior is reproduceable after performing a suspend-to-RAM (eg. closing the lid, or via right-clicking-on-battery-icon-in-the-system-tray-and-selecting-'Suspend'-from-the-popup-dialog)

**hardware-wise:**
    - Thinkpad T60 ([click here for specs]("http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=2613eau&sitestyle=lenovo"))

**software-wise:**
    - Kubuntu 7.04 (Feisty Fawn)
    - stock kernel (2.6.20-15-generic)
    - stock ipw3945 driver (1.2.0mp) and userspace daemon (ipw3945d-2.6.20-15-generic v1.7.22)
    - wireless is configured with wireless-tools (via command line), not (K)NetworkManager

**brief configuration notes:**
    - WPA manually set up for my LAN at home
    - eth0 is configured for my work LAN

Here's a log of commands as I normally observe it:

(before suspend-to-RAM, eth1 working and identified by 'iwconfig')
```

emparq@onyx:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:57   Missed beacon:0

```

(after waking up from suspend-to-RAM, eth0 is now gone, and eth0 is now the wireless adapter as identified by 'iwconfig')
```

emparq@onyx:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7674   Missed beacon:0

emparq@onyx:~$ ls -la /sys/class/net/eth0/device/driver/module
lrwxrwxrwx 1 root root 0 2007-05-19 21:41 /sys/class/net/eth0/device/driver/module -> ../../../../module/ipw3945

```

A workaround for me seems to be **rebooting with the ethernet port plugged in**. After that, my eth1 comes up properly, and I can connect again (the plug doesn't have to be in after that, it just needs to be connected during the bootup process- most likely for when the kernel is loading the e1000 driver for my gigE adapter).

Rather unfortunate solution, I know, but there it is. Hopefully someone else knows a way to fix this problem.

---

### Post by emparq on 2007-05-31
Just wanted to follow up, I found [this thread]("http://ubuntuforums.org/showthread.php?t=238323") which lead me to my solution at Lenovo's support site [here]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-67166").

So to recap:
- after resuming from a suspend, the Intel PRO/1000 ethernet adapter causes an error (see [here]("http://www.thinkwiki.org/wiki/Problem_with_e1000:_EEPROM_Checksum_Is_Not_Valid#Problem_Description") for more details)
- this causes eth1 to become eth0 (and thus, eth1 'disappears')
- running the script found at that Lenovo support page is a one-time-run kind of fix
- what this script seems to do is correct the bytes in the EEPROM that cause this problem (so this script actually might or might not work for other Intel-based chipsets using the Intel(R) PRO/1000 and Intel(R) PRO/Wireless 3945 adapters)

Hope this helps somebody out there.

---

### Post by torpedo on 2007-06-19
If you have this problem on a lenovo thinkpad x60s:

hi all. I am posting because this may help somebody. It's ludicrous.

I have been having problems similar to those reported here with my wireless on thinkpad x60s. All of a sudden the wireless was not on network manager. But my wireless device was ok, the driver was loaded, kept on getting no wireless when typing iwconfig. I won't bother you with all the things I tried, but basically it has to do with the

Kill switch must be turned off for wireless networking to work.

business. Well, if you got there, turns out the thinkpad x60s has a f**king physical switch that turns the wireless on and off, it's a tiny thing located in front of the machine, very front towards you, just under the keyboard. For some reason that switch had moved, but I wasn't even aware of its existence. It must have happened while travelling. Turn it on, and ubuntu (at least Feisty) will work beautifully like before.

Unbelievable.

---

### Post by zdu on 2007-07-02
I had this same problem with my new dellbuntu Inspiron E1505 notebook.  Going through the steps in the dialog posted by Fogge + reboot  + Fn-F2 worked for me.  Its working great, only difference is that eth0 <-> eth1 swapped.

This is one reason open-source rocks ... support via Google beats waiting on hold for an hour for a level-1 tech to ask if the wireless modem is plugged in and then requesting power-cycling on the modem!

Thanks a lot for posting the complete dialog.

-zerksis :)
=====

---

