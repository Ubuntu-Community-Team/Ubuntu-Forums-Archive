---
title: "Printing HP Envy 5540"
date: 2020-01-30
forum: Hardware
---

### Post by Philip_Edwards on 2020-01-30
Hi Group,
I have Lubuntu (16.04 I believe.)
HP 530 laptop. Everything is working just fine.....but maybe I'm trying to be too adventurous here.
I'm trying to connect it to my HP Envy 5540 printer.

I've installed CUPS.

Printers finds my printer on the network.
It appears to have installed some sort  of generic driver.

Anyway, I can tell the computer to print and it goes through all the normal I'm about to print something stages..........and nothing happens.

Any suggestions?

Phil

---

### Post by slickymaster on 2020-01-30
*Thread moved to **Hardware**.*

---

### Post by CelticWarrior on 2020-01-30
Install ```
hplip
``` and ```
hplip-gui
``` for better control.

---

### Post by brian_p on 2020-01-30
It would be useful to have the putput of ```
driverless
```

---

### Post by guiverc on 2020-01-30
Lubuntu 16.04 LTS, being a flavor of Ubuntu, had only 3 years of supported life and is now EOL.

Ubuntu 16.04 LTS with Unity (7) desktop, server with no desktop, or Kylin desktop came with 5 years of support. All other flavors had only 3 years of support.

> [COLOR=#333333]Maintenance updates are provided for 5 years for Ubuntu Desktop, Ubuntu Server, Ubuntu Cloud, Ubuntu Base, and Ubuntu Kylin. All the remaining flavours are supported for 3 years.[/COLOR]  [http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/](http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/)

> [COLOR=#555555][FONT=Ubuntu]Lubuntu 16.04 LTS will be supported until April 2019, with three years of support.[/FONT][/COLOR]  [https://lubuntu.me/xenial-released/](https://lubuntu.me/xenial-released/)

I'd suggest checking your system release, using `ubuntu-support-status` to verify what percentage of your system is still supported, and consider upgrading to a supported release if you are in fact using Lubuntu 16.04 LTS or a release that is *end-of-life*&#8203;.

---

### Post by Philip_Edwards on 2020-01-30
```
philip@philip-HP-530-Notebook-PC:~$ hplip
hplip: command not found
philip@philip-HP-530-Notebook-PC:~$ hplip-gui
hplip-gui: command not found
philip@philip-HP-530-Notebook-PC:~$
```

---

### Post by Philip_Edwards on 2020-01-30
```
philip@philip-HP-530-Notebook-PC:~$ driverless
driverless: command not found
philip@philip-HP-530-Notebook-PC:~$
```

---

### Post by slickymaster on 2020-01-30
> **Philip_Edwards said:**
> ```
philip@philip-HP-530-Notebook-PC:~$ hplip
hplip: command not found
philip@philip-HP-530-Notebook-PC:~$ hplip-gui
hplip-gui: command not found
philip@philip-HP-530-Notebook-PC:~$
```

Thing is you have to install those packages```
sudo apt update
sudo apt install hplip hplip-gui
```

---

### Post by yancek on 2020-01-30
In post 3 above, it was suggested that you install hplip and hplip-gui not that you type those commands in a terminal.  The link below has a download link for various distributions and has a link for the install instructions.

[https://developers.hp.com/hp-linux-imaging-and-printing/gethplip](https://developers.hp.com/hp-linux-imaging-and-printing/gethplip)

---

### Post by CelticWarrior on 2020-01-30
> **Philip_Edwards said:**
> ```
philip@philip-HP-530-Notebook-PC:~$ hplip
hplip: command not found
philip@philip-HP-530-Notebook-PC:~$ hplip-gui
hplip-gui: command not found
philip@philip-HP-530-Notebook-PC:~$
```

That's why I said **install them**.

> **Philip_Edwards said:**
> ```
philip@philip-HP-530-Notebook-PC:~$ driverless
driverless: command not found
philip@philip-HP-530-Notebook-PC:~$
```

This suggests deeper problems because that command should exist in a default installation.
And please do not ignore post #5.

---

### Post by brian_p on 2020-01-30
> This suggests deeper problems because that command should exist in a default installation.

Not really; it is more an indication that brian_p has been lax (once again :(). The *driverless* utility does not exist on Ubuntu 16.04. It appeared in 18.04. with cups-filters.

However, the 5540 is supported by hplip on xenial.

---

### Post by Philip_Edwards on 2020-01-30
You have 24 packages (1.7%) supported until April 2021 (Community - 5y)
You have 1163 packages (83.1%) supported until April 2021 (Canonical - 5y)

You have 0 packages (0.0%) that can not/no-longer be downloaded
You have 212 packages (15.2%) that are unsupported

Run with --show-unsupported, --show-supported or --show-all to see more details
philip@philip-HP-530-Notebook-PC:~$ c

---

### Post by brian_p on 2020-01-30
If your objective is to be able to print *now* (and consider updating at a later time), we need some information. For a start, what you get for ```
lpinfo -v
```.
You are using a USB connection?

---

### Post by Philip_Edwards on 2020-01-31
OK. Thanks for helping me.

I've downloaded and installed the hplip package.

I think I've followed the installation instructions on this page  

[https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index](https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index)

I have hplip-3.19.12.run on my desktop.

Now, I tried this in Terminal and got this.

philip@philip-HP-530-Notebook-PC:~$ sh hplip-3.19.12.run
sh: 0: Can't open hplip-3.19.12.run

---

### Post by brian_p on 2020-01-31
> **Philip_Edwards said:**
> OK. Thanks for helping me.

I've downloaded and installed the hplip package.


Why, oh why, when everything you need is already on your system.

---

### Post by Philip_Edwards on 2020-01-31
It might be on the system, but my printer still doesn't print.

---

### Post by ajgreeny on 2020-01-31
Several things you can try listed below.
[LIST=1]
[*]Check that the hplip-3.19.12.run file is executable in its properties.
[*]Make sure when you try to run it that you are already in the folder where it sits.
[*]If you got a full error message when trying to run the installer give us all details; your output of ***sh: 0: Can't open hplip-3.19.12.run*** is not very helpful and I would expect more about the reason why.
[*]You might also try using ***bash*** in place of ***sh*** in your command.
[/LIST]

You could also ignore your downloaded run file and simply install the packages from the repos with (as has been mentioned before) ```
sudo apt install hplip hplip-gui
```
The repo version is good enough for that printer and should give you full use.

---

### Post by brian_p on 2020-01-31
> **Philip_Edwards said:**
> It might be on the system, but my printer still doesn't print.

You may not have seen my previous post, so I will repeat it:

What you get for
```
lpinfo -v
```

You are using a USB connection?

---

### Post by Philip_Edwards on 2020-01-31
Thanks everybody.

After an update to 18.04 everything works fine.

Phil

---

### Post by brian_p on 2020-01-31
> **Philip_Edwards said:**
> Thanks everybody.

After an update to 18.04 everything works fine.

Phil

This is my final involvement with users on 16.04. From now on they will be requested to upgrade to 18.04 first.

---

### Post by Yellow Pasque on 2020-02-01
Please mark the thread SOLVED (Thread Tools menu above first post).

> **brian_p said:**
> This is my final involvement with users on 16.04. From now on they will be requested to upgrade to 18.04 first.

Ubuntu 16.04 is supported for another year. If you personally don't want to help people running 16.04, that is your choice, but I don't think automatically telling them to upgrade is helpful, unless you truly believe the problem is caused by the older version (e.g. they're trying to use very new hardware on 16.04).

---

### Post by brian_p on 2020-02-01
> **Yellow Pasque said:**
> Please mark the thread SOLVED (Thread Tools menu above first post).

Ubuntu 16.04 is supported for another year. If you personally don't want to help people running 16.04, that is


You will note from my posts (and those of others) that I believed the problem was sortable within 16.04. Philip_Edwards has a different belief system and an adversion to answering questions.

> 
your choice, but I don't think automatically telling them to upgrade is helpful, unless you truly believe the problem is caused by the older version (e.g. they're trying to use very new hardware on 16.04).

It was a bit over the top, eh? I deserve to have my knuckles rapped. I'll amend it to "possibly ignore users on 16.04". Printing on 18.04 is far more straightforward anyway, on the whole, and easier to deal with.

---

