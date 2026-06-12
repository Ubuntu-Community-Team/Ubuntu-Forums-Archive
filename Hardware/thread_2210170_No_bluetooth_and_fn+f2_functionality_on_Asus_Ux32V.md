---
title: "No bluetooth and fn+f2 functionality on Asus Ux32VD"
date: 2014-03-09
forum: Hardware
---

### Post by rasmus91 on 2014-03-09
Hello. The title pretty much says it all.

I have an Asus UX32VD, a small laptop that i'm incredible satisfied with. The only thing that seems not to be working Under Ubuntu (other than the lighting sensor) is the bluetooth module. It just won't turn on. 
I follow the instructions on [this thread]("https://help.ubuntu.com/community/AsusZenbookPrime"), pressing fn+f2 to turn on and off wireless signals, but it doesn't register that combo, even when all the other FN+f-something combo's seem to be working.

Does anyone have some insight on this? it's actually quite annoying, and i haven't been find an answer as no one else seems to have reported this particular problem.

I'm running Ubuntu 13.10 64bit.

thank you for reading.

---

### Post by varunendra on 2014-03-10
Actually, the Fn+F2 not working on Asus notebooks/netbooks is a common problem for quite some time now. A couple of bug reports have been submitted, and quite a few people have added themselves to their "Affects Me" list. I'd request you do the same if you happen to have the same bug (and I'm 100% sure it is).

Please see this thread to verify if you have the same bug, and the workaround for it : [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

If you have a launchpad account, or can take a few minutes to create one, please add yourself to the linked bug reports there, as well as adding your comments/diagnostics-report to them to help getting it resolved faster. Thanks!

---

### Post by rasmus91 on 2014-03-13
My WiFi has at all times worked in ubuntu with the laptop, can it still be this problem?

---

### Post by varunendra on 2014-03-14
The same driver "asus_nb_wmi" controls both wifi and bluetooth. Although I initially thought your problem is wireless related, and my suggestion was based on that assumption. But the same approach may work here too.

As quoted in **[this post]("http://ubuntuforums.org/showthread.php?p=12785026#post12785026")**, the suggested value "1" changes the control of "bluetooth/WLAN" to "hardware/software", which works for wireless issues.

As mentioned in the same quote, the value "4" (most of the time, not always) changes the control to "software/software". Accordingly, please try -
```
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
```
Reboot to see if the bluetooth is enabled (or can be enabled with "sudo rfkill unblock all" command). If not, you may try other values (anything from 1 to 9, as 0 is default).

If there is no difference with any of the values, it could mean that the problem may be with the bluetooth stack itself, not the wmi control. Delete the .conf file in that case, since it would be useless -
```
sudo rm /etc/modprobe.d/asus_nb_wmi.conf
```

And let us know how beautifully it failed.

---

### Post by rasmus91 on 2014-03-20
It worked. Bluetooth is enabled now, and i was able to pair it with my phone.

can you help me get the fn+f2 combo working as well? :)

It looked like my internet connect got slower by it, but that might be the fact that they are using microsoft forefront where i am, and that is... safe to say a poor experience almost after every reboot.

---

### Post by varunendra on 2014-03-21
> **rasmus91 said:**
> It worked. Bluetooth is enabled now, and i was able to pair it with my phone.
That is an exciting news for me! I hope it was the parameter trick, not a coincidence, that did the trick. :)

> can you help me get the fn+f2 combo working as well? :)
Unfortunately, that seems to be a bug that is still unsolved. For a possible workaround, please try post #2 of the same thread I linked to previously. Let me know if you need specific help with the 'workaround'.

*(I may or may not get enough time to be on the forums for a few days, so if you posted and I couldn't reply, feel free to ask (by PM) other experts to help you with that..)*

> It looked like my internet connect got slower by it, but that might be the fact that they are using microsoft forefront where i am, and that is... safe to say a poor experience almost after every reboot.
Most of the bluetooth adapters are embedded on the same card as the wifi these days, and it 'Always' works within the same frequency range as most wifi's (2.4 GHz). So if both are enabled at the same time, they may cause mutual interference.

Some wireless drivers provide a parameter "bt_coex.." which helps avoiding this interference. So if your driver is such one, you may try that parameter (I'd be glad to help with that as well). Although being able to switch off the bluetooth when you are not using it would be a better solution. The post #2 I referred above may be able to help with that.

To see which card and driver you are using, please post the output of -
```
lspci -nnk | grep -iA2 net
```

To block ONLY bluetooth with "rfkill command", you may try -
```
sudo rfkill block bluetooth
```
(you may alternatively bind the same command with "xbindkeys" if you try that workaround).

---

### Post by rasmus91 on 2014-04-04
Sorry for taking so long in replying, i've been meaning to for a while.
here's the output:

```
lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
	Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
	Kernel driver in use: iwlwifi

```

I've noticed that most of the fn combinations that i used before activating bluetooth doesn't seem to work anymore. This includes turning the keyboard backlight up and down, as well as disabling the touchpad. sometimes, volume control seems lagging too, this is really annoying, as this is more important to me than the bluetooth.

anyhow, thanks for your time.

---

### Post by varunendra on 2014-04-05
As far as I know, the 'asus_nb_wmi' driver deals with only radio devices - the wireless and bluetooth. If that is true (I'm not very sure), the change we tried (wapf=4) shouldn't affect anything else at all. But it's easy to verify that, simply delete the .conf file and see if everything becomes as it was before -
```
sudo rm /etc/modprobe.d/asus_nb_wmi.conf
```
Reboot and see the effect. Depending on the result and your preference, you may choose to recreate or not to recreate the conf file again.

In my personal experience, the Fn+ combos for backlight, volume control and touchpad seem to depend on "asus_wmi" driver, not "asus_nb_wmi". So if that one is loading correctly, these combos should work perfectly. But yes, there may be some sort of interference or miscommunication due to the change we tried. The above test (removing the conf file) should confirm whether or not that is the case.

By the way, your driver 'iwlwifi' does offer the option to disable the "bluetooth coexistence" feature. To try that (after sorting out above, to eliminate any possible confusion), try this parameter -
```
echo "options iwlwifi bt_coex_active=N" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
The change will take effect after a reboot or after manually reloading the driver by the following command -
```
sudo modprobe -rv iwldvm iwlwifi
sudo modprobe -v iwldvm
```

To verify whether the parameter took effect or not -
```
cat /sys/module/iwlwifi/parameters/bt_coex_active
```
The output should be "**N**". If it is, test your wifi and see if the performance is any better now.

---

### Post by rasmus91 on 2014-04-22
after doing:
```
sudo rm /etc/modprobe.d/asus_nb_wmi.conf
```

I get the fn+f combos working again, with the exception of fn+f2 (go figure), and another interesting thing occurs: My bluetooth seems to remain active.

Also: the WiFi performance doesn't seem to really suffer any problems as long as i click the bluetooth icon and disable it (through the GuI) want me to try that other thing all the same?

---

### Post by varunendra on 2014-04-22
The suggested parameter (bt_coex_active=N) would make any difference only in the scenario when both wifi and bluetooth are working at the same time. If you are okay with disabling BT while using wifi, then no, you don't need that extra step.

---

