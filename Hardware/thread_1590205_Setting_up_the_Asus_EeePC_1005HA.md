---
title: "Setting up the Asus EeePC 1005HA"
date: 2010-10-07
forum: Hardware
---

### Post by ryukent on 2010-10-07
Setting up the Asus EeePC 1005HA

The EeePC 1005HA does not work 100% out of the box at the time of writing so I've collected info from a number of sources that you may find useful. 

Setting up the hotkeys:
Hotkeys don&#8217;t work by default, you have to add a kernel parameter to the grub config. This will allow the FN+x button combination to disable wireless, adjust volume etc. It doesn't do power options though:

Run &#8216;sudo gedit /etc/default/grub&#8217;

Edit the line with GRUB_CMDLINE_LINUX_DEFAULT and add &#8221; acpi_osi=Linux&#8221;.

The line should then look like -> GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash acpi_osi=Linux&#8221;

Save and then run &#8216;sudo update-grub&#8217;

Reboot

Installing EeePC tray application:
This will install the small tray icon that allows you to set power policies and change resolutions etc.

Setup the statux.org repository by adding the following line to /etc/apt/sources.list.

deb [http://www.statux.org/software](http://www.statux.org/software) packages main

Now, add the appropriate signing key to ensure that the packages you are downloading are signed by statux.org

wget -q [http://www.statux.org/software/key/statux.pub](http://www.statux.org/software/key/statux.pub) -O- | sudo apt-key add -

Update your package list with

sudo apt-get update

Then install the necessary package with 

sudo apt-get install eeepc-tray

Keeping battery life to a maximum:
Ubuntu seems to use a lot of battery when compared to windows but it is possible to enable laptop-mode and reduce the power consumption. Powertop is a program that can be used to monitor the amount of power consumed.

sudo apt-get install laptop-mode-tools powertop

Laptop mode will be installed automatically, you will need to run powertop using

sudo powertop

---

### Post by superninja on 2010-10-31
Is this in netbook remix 10.10? Or does it matter?

---

### Post by Monicker on 2010-11-23
Thanks! Was wondering why my function keys had stopped working after upgrading to 10.10.

---

### Post by Nubnut on 2010-12-01
Thanks for your help*with this ryukent!

Although I'm not sure that the statux.org repositories are still working, they're showing as a "failed" when Update Manager is run.

I'm on a 10.04 LTS and had the original statux repos (for atheros wireless back then) which I think allowed me to now install powertop and eeepc-tray..

Thanks Again

Nubnut;)

---

### Post by Krompel on 2010-12-09
> **ryukent said:**
> Setting up the Asus EeePC 1005HA

"blabla"

Setup the statux.org repository by adding the following line to /etc/apt/sources.list.

deb [http://www.statux.org/software](http://www.statux.org/software) packages main

-- done

> **ryukent said:**
> Now, add the appropriate signing key to ensure that the packages you are downloading are signed by statux.org

wget -q [http://www.statux.org/software/key/statux.pub](http://www.statux.org/software/key/statux.pub) -O- | sudo apt-key add -

-- Here something seems to go wrong. When I enter this exact command (assuming -O- is a capital o, the letter before the p in the alphabet) I get this response: "gpg: no valid OpenPGP data found."
Does this mean the file is not available anymore?

> **ryukent said:**
> Update your package list with

sudo apt-get update

"blabla"

If anyone knows what mistake I am making or how to fox this, please tell me?

Greetings!

---

