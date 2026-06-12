---
title: "Remove and re-install Brother printer"
date: 2012-02-11
forum: Hardware
---

### Post by pottzie on 2012-02-11
I'm using Ubuntu 11.10, and when I upgraded to 11.10, somehow I lost the printer. I've read that this model is supported (Brother HL-2040), but it doesn't work, so I'm resorting to doing it the way I had to install it to my earlier version of Ubuntu.
 I went to the Brother website and downloaded the cups driver and the Brother driver for my printer and installed them using apt-get install. That went OK, but the printer still doesn't print, and its'showing two jobs waiting to be printed from before I downloaded the drivers. I think I need to remove the printer and re-install it, but when I bring up the printers dialog box, I don't find any way to remove the printer. Anyone know how to get this thing to work?

---

### Post by jerrrys on 2012-02-11
Have you seen this?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Brother+HL-2040+oneiric+11.10&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Brother+HL-2040+oneiric+11.10&sa=Search&cof=FORID:9)

---

### Post by bluexrider on 2012-02-11
I think kernel 3.0.0-14 fixes this problem. Have you done a ```
sudo apt-get dist-upgrade
``` yet?

---

### Post by pottzie on 2012-02-11
I ran apt-get dist-upgrade, but it didn't include a new kernel. I forget what the command is to see which kernel I'm using.

 Edit: Just re-booted to see which kernel I'm using. Turns out it's 3.0.0.15.

---

### Post by jerrrys on 2012-02-11
> **pottzie said:**
> I ran apt-get dist-upgrade, but it didn't include a new kernel. I forget what the command is to see which kernel I'm using.

ls /boot

---

### Post by pottzie on 2012-02-11
Yep, it shows vmlinuz-3.0.0-15-generic

---

### Post by bluexrider on 2012-02-11
> **pottzie said:**
> Yep, it shows vmlinuz-3.0.0-15-generic

Well, that isn't the issue now is it.

Brother web site for linux printer drivers here:  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2040](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2040)

---

### Post by pottzie on 2012-02-11
Yep, I've downloaded the two drivers (cups and Brother) and installed them from the Downloads directory using apt-get install...

 They both seemed to install OK, just that the printer, as it was before downloading the drivers, still shows two jobs (print test page) in the Que. But I can't uninstall the printer or even get rid of the two pending print jobs by right-clicking on them.

---

### Post by bluexrider on 2012-02-11
If the correct print drivers are installed I would try turning off the printer, rebooting and then turning the printer back on after Ubuntu has loaded.

You might try clearing the queue using cups  [http://localhost:631/](http://localhost:631/)

---

### Post by pottzie on 2012-02-11
I forgot about localhost631. When I checked, it shows the printer as "paused." I think I saw that under the "Printers" dialog box for Ubuntu, too. I can see that the printer is turned on, and I "assume" that it's connected properly, since nothing that I know of changed other than upgrading Ubuntu.
 ...However...when I try "lsusb" in the terminal, I don't see any printer. Hmm..

Edit: Went back and took a lookat the "631" page. It said to run lpstat -p -d and see what printers it showed. The result:

printer HL-2040-series disabled since Sat 11 Feb 2012 07:18:22 PM EST -
	Paused

---

### Post by bluexrider on 2012-02-12
> **pottzie said:**
> I forgot about localhost631. When I checked, it shows the printer as "paused." I think I saw that under the "Printers" dialog box for Ubuntu, too. I can see that the printer is turned on, and I "assume" that it's connected properly, since nothing that I know of changed other than upgrading Ubuntu.
 ...However...when I try "lsusb" in the terminal, I don't see any printer. Hmm..

Edit: Went back and took a lookat the "631" page. It said to run lpstat -p -d and see what printers it showed. The result:

printer HL-2040-series disabled since Sat 11 Feb 2012 07:18:22 PM EST -
    Paused
So, does this mean you re-enabled it and are no able to print?

---

### Post by kurt18947 on 2012-02-12
It may not matter but Brother recommends using dpkg -i vs. apt-get install.  I do know that for 64 bit OSs I need to do 
Command (for dpkg)  : 
```
 dpkg  -i  --force-all  (lpr-drivername or cups-drivername)
``` plus all the 'before you install' stuff.  Sorry if you already know this stuff.

---

