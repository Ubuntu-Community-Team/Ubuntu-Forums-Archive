---
title: "ubuntu wifi problem after hibernate"
date: 2009-04-22
forum: Hardware
---

### Post by xbenes2 on 2009-04-22
Hello,
 I have the following problem with my umax laptop/jaunty RC. All works great until I hibernate and wake it up again. The PCMCIA network card seems to be present after this wakeup (after "ip link" command it can be seen) but network manager cannot find any networks. I did some investigations and tried this:
sudo iwlist scan
Failed to read scan data : Resource temporarily unavailable. 

Nevertheless, after suspend or reboot the networks are detected afterwards and the command "sudo iwlist scan" is able to find all networks. 

Seems like jaunty does not wake up properly from hibernate (although wakes up properly from suspend). I tried sudo /etc/init.d/networking restart and also restarting gnome network manager, I tried putting interface up and down, nothing helped. After reboot (or suspend&wake) it works again.

Thanks for any suggestions. Petr

---

### Post by sidewalkcynic on 2009-04-22
I'm sure I have seen this problem described several times throughout the course of my year on Linux - I don't think there's a fix.

---

### Post by mvdberg112 on 2009-04-22
I've had trouble with hibernate (did not use so much Standby) of anotehr nature, but the wireless always worked. I am using Netgear WG111v2 with rtl8187 driver.

Check what your driver is with 
 # lsmod
What is your card model? Is there a driver with the same or similar name?
If not, try this:
unplug adapter
reboot system
run #lsmod
plug adapter
run #lsmod
Which extra drivers are present in the list?

What you might try is this:
 # ifdown --force wlan0
 # modprobe -v -r <driver name> (unloads the driver)
for me that would be modprobe -v -r rtl8187
 # modprobe -v <driver name>
 # ifdown --force wlan0
 # ifup --force wlan0
 Send us a # dmesg | tail -n 50 at this point
 # iwconfig wlan0 essid MyNetworkName
 check if the link is up with # dmesg | tail 
 # dhclient wlan0

This worked for me when I had troubles with the drivers; you might try it after hibernate and check dmesg to see if you see something interesting. Use it also just after the hibernate: maybe there is a message that explains it.

---

### Post by xbenes2 on 2009-04-22
Thanks for replies, reloading modules seems to be a good way. Extra modules loaded (my lucent/orinoco wireles pcmcia card) are:

orinoco_cs
orinoco
hermes_dld
pcmcia
yenta_socket
rsrc_nonstatic

However when I try to remove modules and load them again, I get the following message:
#modprobe -v -r orinoco_cs 

FATAL: Module orinoco_cs is in use.

Unfortunately i cannot find out how to force module removal.
If I try #rmmod -f orinoco_cs I get similar message as in my first post when scanning for wireless networks:

#rmmod -f ERROR: Removing 'orinoco_cs': Resource temporarily unavailable

EDIT: rmmod worked only when the PCMCIA card was ejected from the slot.

EDIT: Finally I do not know what happened, after experimenting with these modules I have discovered a simple solution :-) If I insert the PCMCIA card into the slot before turning on my laptop, it is recognised and it works. This is ok for me. Thank you all again.

---

### Post by dolphin_oracle on 2009-04-22
That is similar behavior that I used to get with removable cards.  If you want to take the card out (say before it goes in your bag), make sure to disable the card BEFORE hibernating.  Nothing breaks it faster than waking up from hibernate looking for hardware that isn't there.

---

### Post by GOwin on 2009-04-28
Good to hear you found a fix.

I have a similar problem since Hardy with the built-in Ralink RT2500 card. I also tried disabling the wireless before I got to suspend/hibernate, but that doesn't work either. It will disappear after hibernating, and will not work unless I reboot. 

Which kinda defeats the purpose of hibernating/suspending don't you think?

---

