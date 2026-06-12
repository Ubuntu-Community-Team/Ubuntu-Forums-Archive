---
title: "Sound card assignment"
date: 2008-11-01
forum: Hardware
---

### Post by rgeddes on 2008-11-01
Hi,

I have two sound cards in my system, one built in and one I installed, a Delta 66 sound card (snd_ice1712 driver).  I want to use the Delta 66 for my daily sound consumption and found a way to configure this in pulseaudio (PA) so that I alias hw:0 to the built-in card, and hw:1 to the Dela 66.

This setup worked consistently until a few upgrades ago.  I assume that the system would assign hw:0 to the built-in and then hw:1 to the Delta 66. 

I can tell which card gets assigned which number by executing:

```
ls -l /proc/asound/ | grep '^l'
lrwxrwxrwx 1 root root 5 2008-11-01 08:18 M66 -> card0
lrwxrwxrwx 1 root root 5 2008-11-01 08:18 NVidia -> card1

```

The symbolic links show which card got which number.  This time, the card number is in the wrong order.

Now, when my system starts, there seems to be a random assignment.  Sometimes the Delta 66 is assigned hw:0 and sometimes it's assigned hw:1.

Is there a way to control which card is assigned which number?

BTW, do those numbers n, as in hw:n, have an official name?

Thanks,
Richard

---

### Post by rgeddes on 2008-11-20
I was tinkering around with this issue again, and I found that the command:

alsactl names

does not perform as advertised.

What it's supposed to do(from man alsactl) :


> names generates list of available device names for applications.  The card number or id is ignored for this command. The list is always  generated for all available cards.


On first execution I got:
```
$0> alsactl names
alsactl: generate_names:538: Cannot open /etc/asound.names for writing: Permission denied
```

So the "names" command tried to write the current state of the alsa sound configuration to the /etc/asound.names file.  I verified this by making a backup of my default /etc/asound.names file...  ```
cp -p /etc/asound.names /etc/asound.names.backup
```, ran the command with sudo... ```
sudo alsactl names
```,  and compared... ```
diff /etc/asound.names /etc/asound.names.backup
```

I'm trying to change the the card assignment without rebooting... the assignment can be seen by the soft link assignments of "ls /proc/asound/".  I stopped the the alsa sound server... ```
sudo /etc/alsa-utils stop
```,  but the entries in the /proc/asound/ stayed the same. Tried deleting the /proc/asound directory... that didn't work... system won't allow deleting that directory even with sudo... Tried ```
sudo alsactl restore
```... that didn't reassign the card numbers either.  

Any ideas?

Regards,
Richard

---

### Post by ljuksi on 2008-12-11
I found a solution: 
edit the file "/etc/modprobe.d/alsa-base"

  sudo nano /etc/modprobe.d/alsa-base 

add the index=<n> to the options for the driver of your card, for example:

  options snd-hda-intel index=0 position_fix=0 model=ref
  options snd-ice1712 index=1

finally, reload alsa:
  
  sudo alsa reload

Hope this helps!

---

