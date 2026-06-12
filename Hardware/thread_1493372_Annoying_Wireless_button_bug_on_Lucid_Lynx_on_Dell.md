---
title: "Annoying Wireless button bug on Lucid Lynx on Dell Vostro 1320"
date: 2010-05-25
forum: Hardware
---

### Post by krippa on 2010-05-25
First I couldnt understand why the wireless was only working every now and then. I had already installed the proprietary Broadcom driver that usually fixes any issues but suddenly I could not connect at all.

I then realized it is because of the wireless button on this Vostro 1320 that I just bought. What happens is Ubuntu detects whatever position it's in when ubuntu boots as being the off-position. If this really is the hardware-off, everything works when you switch it to the on-position. 

If I boot with the wireless button in the on-position however, NetworkManager stubbornly insists that wireless is turned off (the activate wireless network is greyed out when right-clicking the icon) even though the blue wireless diode is on. When I move the switch to the off-position, NetworkManager shows wireless as being active but since the hardware switch is now off, no networks are found..

Any ideas on how to fix/further troubleshoot this?
Can I "fool" NetworkManager to believe that wireless is always on?

Thanks,
Kris

Edit: It also happens on suspend/resume. e.g. I have to turn off wifi switch before going to suspend or it wont work..

---

### Post by krippa on 2010-06-06
After some further troubleshooting and searching around I realized that the problem was with the rfkill package which doesnt properly detect the position of the wireless switch unless I turn the computer on with the switch OFF. I filed a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/rfkill/+bug/588366").

For anyone looking for a workaround to this or similar problems I managed to work around the problem by "fooling" rfkill to read my static values on a mounted tmpfs instead of reading values provided by the driver (or whatever normally provides the values. I put all the necessary commands in a script to be run on startup. Here we go:

1. Get your system in a state when wireless block is off (you can check with "rfkill list" in terminal). If wou cannot do this copy whatever you can get and try to change value of "state" to 1 when you copied it in step 2. 
2. Copy current state to a folder of your choice (I chose a folder in the /home dir but there is probably som better place):
sudo cp -r/sys/devices/virtual/rfkill/rfkill0/ /home/rfkill_fix/
3. Create the script that overrides default behavior by mounting a tmpfs over the /sys/devices..., copies the files from step 2 to tmpfs and restarts network-manager:
sudo gedit /home/rfkill_fix/fix_wireless.sh
and paste:
```

mount -t tmpfs -o size=1M tmpfs /sys/devices/virtual/rfkill/rfkill0
#Note that you may need to change first folder dep on where you copied the files
cp -r /home/lilhana/rfkill0/* /sys/devices/virtual/rfkill/rfkill0/
restart network-manager
```
4. Make the script executable:
sudo chmod +x fix_wireless.sh
5. Make sure the script runs on startup (as root):
sudo gedit /etc/rc.local
and add a reference to the script you just created before the "exit" line:
```
echo "Working around wireless bug"
/home/rfkill_fix/fix_wireless.sh
```

Hope this helps someone..

---

### Post by ctothej on 2010-07-10
I was able to fix the issue by issuing the command
```
rfkill unblock 0
```
even though I have no clue why it worked yet.

---

### Post by condamine on 2010-07-14
Ditto - I have no clue why - but this also re-enabled the Wireless network.

```
rfkill event
```
...toggle the switch: watch live update of event info

I'm using a Dell Studio 15 (Ubuntu 10.04.1 Lynx) and my experience of having the wireless network disabled seems to occur after any upgrade (using the Upgrade tool) - but I will do some testing to see if it is, as Krippa says, related to the state of the wireless at reboot. BTW this Dell has a keyboard key combination on/off switch rather than an actual hardware switch. This works when up and running - I can disable and re-enable both Bluetooth and WiFi with the keyboard command.

This didn't happen with Ubuntu 9.10 (Karmic); I had other issues (not detecting my wireless router) in Karmic that have been greatly improved in Lynx.

---

### Post by hsifyppah on 2010-08-16
Krippa, thank you so much for the workaround!  This bug has been driving me nuts since koala.

---

### Post by dizzyguy209 on 2010-12-14
Thanks so much krippa, this was so annoying


> **krippa said:**
> After some further troubleshooting and searching around I realized that the problem was with the rfkill package which doesnt properly detect the position of the wireless switch unless I turn the computer on with the switch OFF. I filed a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/rfkill/+bug/588366").

For anyone looking for a workaround to this or similar problems I managed to work around the problem by "fooling" rfkill to read my static values on a mounted tmpfs instead of reading values provided by the driver (or whatever normally provides the values. I put all the necessary commands in a script to be run on startup. Here we go:

1. Get your system in a state when wireless block is off (you can check with "rfkill list" in terminal). If wou cannot do this copy whatever you can get and try to change value of "state" to 1 when you copied it in step 2. 
2. Copy current state to a folder of your choice (I chose a folder in the /home dir but there is probably som better place):
sudo cp -r/sys/devices/virtual/rfkill/rfkill0/ /home/rfkill_fix/
3. Create the script that overrides default behavior by mounting a tmpfs over the /sys/devices..., copies the files from step 2 to tmpfs and restarts network-manager:
sudo gedit /home/rfkill_fix/fix_wireless.sh
and paste:
```

mount -t tmpfs -o size=1M tmpfs /sys/devices/virtual/rfkill/rfkill0
#Note that you may need to change first folder dep on where you copied the files
cp -r /home/lilhana/rfkill0/* /sys/devices/virtual/rfkill/rfkill0/
restart network-manager
```
4. Make the script executable:
sudo chmod +x fix_wireless.sh
5. Make sure the script runs on startup (as root):
sudo gedit /etc/rc.local
and add a reference to the script you just created before the "exit" line:
```
echo "Working around wireless bug"
/home/rfkill_fix/fix_wireless.sh
```

Hope this helps someone..

---

