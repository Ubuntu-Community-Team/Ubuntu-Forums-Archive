---
title: "Which console commands give the same details as HardInfo? (terminal, touchpad, info)"
date: 2012-04-14
forum: Hardware
---

### Post by vezolmi on 2012-04-14
HardInfo is a useful graphical application that shows a lot of information about our computer. I think it gives the details of several terminal commands altogether: lshw, lspci, lsusb, biosdecode, dmidecode ... (if we run these commands with sudo before, at least in some cases, we get more info)

But HardInfo gives more information. E.g. it gives details about the touchpad of the laptop.

Anybody knows which other commands are missing in my list?

Which terminal command(s) show(s) the details about the touchpad?

Thanks

---

### Post by vezolmi on 2012-04-14
The command dmesg gives information about the touchpad. But I think that there should be another command(s) showing details about the touchpad, because HardInfo reflects some data that dmesg doesn't.

Any ideas?

By the way: lsmod also gives some information about the hardware.

---

### Post by vezolmi on 2012-04-14
This command also gives details about the touchpad:
xinput list

Any others?

---

### Post by oldfred on 2012-04-14
Do not know for sure that any of these list what you want or not:

sudo lshw | grep -m 1 -A 25 "*-memory"
For explanation, lshw stands for list hardware, and spits out page after page of information on all the hardware in your machine, this information is then sent to grep, which searches for a key word. I have set a few flags for it, -m 1 which limits the search results to one, saving some time finding additional results when there is only ever going to be one in the hardware output, and -A 25 which sets the number of lines of output after finding the search term to 25(default 0, which wouldn't help here). "*-memory" is there because this is our search term.

If using sudo, run any sudo command like ls first. Sometimes sudo & redirect have issues.
Files saved in your home folder
To save it as a file use
sudo lshw > hw.txt

HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

udevadm info --export-db > file.txt

Similarly, if you run
sudo dmidecode > bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

---

### Post by vezolmi on 2012-04-15
Thanks!

The exact command that has the information (more) that HardInfo reflects in a tidy way in Devices -> Input Devices -> (name of the touchpad) is:

udevadm info --export-db | grep -i -B 5 -A 5 glide
(if the touchpad is called GlidePoint, e.g. if the manafacturer is ALPS)

or

udevadm info --export-db | grep -i -B 5 -A 5 touchp
(if the touchpad is called TouchPad, e.g. if the manafacturer is Synaptics)

---

### Post by vezolmi on 2012-04-15
This command shows more details about the touchpad no matter its manufacturer:
udevadm info --export-db | grep -i -B 9 -A 6 touchp

---

