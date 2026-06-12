---
title: "Installing a new Printer"
date: 2017-01-23
forum: Hardware
---

### Post by DeadlyOats on 2017-01-23
So, I'm installing a Brother DCP-L2540DW printer.  I'm upgrading from a Brother HL-2240 printer.  I followed the instructions [on this page]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=dcpl2540dw_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625").  However, that didn't work.  I kept getting the "command not found" error message on the terminal.

I did some digging and found [this]("http://support.brother.com/g/s/id/linux/en/before.html?c=us&lang=en&prod=dcpl2540dw_us_as&redirect=on#prereq").

So, I tried to run that command, and got the "command not found" error message again.  I think that if I can get _sudo aa-complain cupsd_ working, that I'll be able to install the printer driver....

However, I don't know where to find "sudo aa-complain cupsd" or how to install it....  I need some help to figure this out.

Thanks in advance.

Off topic:

I'm listening to [this]("https://www.youtube.com/watch?v=r0V488DjojI").  I had to share it.  I hope you folks will enjoy it.

[COLOR="#FF0000"]EDIT: (Note to self: Step 1, follow howefield's instructions.  Step 2, follow Bucky Ball's instructions. You have to add "sudo" at the front of the "bash" command.)[/COLOR]

---

### Post by Bucky Ball on 2017-01-24
You're possibly getting the 'command not found' error in the terminal because you have not navigated to the folder where the *_extracted_* driver is or you may not have any software installed to extract this kind of file. More details of your Ubuntu release and flavour, please. 

That driver works fine. You should not need to be faffing around the way you are trying to get it in. It should either install or not. 

There are two commands involved. If they are not working, you are possibly filling in the wrong details.

Navigate in a terminal to where you downloaded the driver. Once there:

```
sudo gunzip linux-brprinter-installer-2.1.1-1.gz
```

You will be asked for a password. You may not need to use 'sudo' at the start at all, but just in case. You must replace the '*.*.*-*' with the version number of the driver exactly as it is shown on the driver you downloaded. You were either getting that wrong or were in the wrong directory?

Once this is extracted and completed:

```
bash linux-brprinter-installer-2.1.1-1 DCP-L2540DW 
```

(You may need to use 'sudo' at the start again).
Again, use the exact driver version number followed by the EXACT model of your device, in this case 'DCP-L2540DW'.

Tell us how you went.

PS: There is a thread called 'What are you listening to now?' for sharing music. This area is for support. :)

PPS: [QUOTE=DeadlyOats]I did some digging and found this.[/QUOTE]

Don't go there, dead end, forget it, you're making more work for yourself and going on a wild goose chase. Those instructions are for a release that has not been supported for six years. Redundant and irrelevant.

---

### Post by DeadlyOats on 2017-01-24
Well, this is exactly what I was doing...  I even shut down the computer, and restarted it, just to be sure.  I followed exactly what you posted, and I kept getting the error messages.  I think I'm using Kubuntu 16.04 LTS.

---

### Post by howefield on 2017-01-24
That command wouldn't be available on a stock install of (x)Ubuntu as far as I can see, you would need to install the package apparmor-utils.

```
sudo aa-complains cupsd
[sudo] password for hugh: 
sudo: aa-complains: command not found
```
```
sudo apt install apparmor-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  apparmor-docs vim-addon-manager
The following NEW packages will be installed
  apparmor-utils
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 52.9 kB of archives.
After this operation, 231 kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 apparmor-utils amd64 2.10.95-4ubuntu5.1 [52.9 kB]
Fetched 52.9 kB in 0s (272 kB/s)         
Selecting previously unselected package apparmor-utils.
(Reading database ... 212991 files and directories currently installed.)
Preparing to unpack .../apparmor-utils_2.10.95-4ubuntu5.1_amd64.deb ...
Unpacking apparmor-utils (2.10.95-4ubuntu5.1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up apparmor-utils (2.10.95-4ubuntu5.1) ...
```
```
sudo aa-complain cupsd
Setting /usr/sbin/cupsd to complain mode.
```

---

### Post by DeadlyOats on 2017-01-24
Thanks, howefield!  Your answer worked!  My printer is working.  Thanks Bucky Ball for taking the time to reply to my post.

---

### Post by howefield on 2017-01-24
Cool, glad it worked for you and thanks for marking as solved.

---

### Post by Bucky Ball on 2017-01-24
Good news and as above. ;)

---

