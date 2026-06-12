---
title: "Not able to boot, BIOS options changed after Ubuntu installed on Fujitsu Laptop."
date: 2018-12-01
forum: Hardware
---

### Post by gauravd-chd on 2018-12-01
Even I am facing something similar. I have Fujitsu laptop (Model: LH532). It had Windows OS. After installing Ubuntu 18.04.1 from USB drive, on restart, laptop just shows "ubuntu" options in boot menu (not showing original BIOS, some new screen). Original BIOS screen does not appear. On selecting "ubuntu" and hitting enter key, nothing happens, so I am stuck with no options to start laptop. Below are the steps that I took.



[LIST=1]
[*]Created bootable USB stick with [https://rufus.akeo.ie/](https://rufus.akeo.ie/) (as recommended on Ubuntu site).
[*]Rebooted the laptop.
[*]Entered BIOS to change boot order so that USB is checked before HDD. Saved BIOS settings and restarted the laptop.
[*]On re-start, options to try or install ubuntu were shown. Selected "try ..." option.
[*]System started with Ubuntu (from USB).
[*]Selected "Install Ubuntu" application icon when system started.
[*]Went through normal question shown in ubuntu installation wizard.
[*]Selected option to customize partitions, as I wanted to remove windows and partition it into two - one for / and another for /home.
[*]Deleted the partition on which Windows was installed (C:\) and divided that into two partitions. One to install root (/) filesystem and another to install /home.
[*]Ubnutu installation started, but after some time got an error "Installer crashed" as Grub could not be installed.
[*]Tried to close the installation window, but nothing happened.
[*]Restarted the system and again booted from USB.
[*]This time I selected "Install ubuntu" option without booting ubuntu from USB in trial mode.
[*]Answered installation questions.
[*]This selected default option (showing reinstall Ubuntu 18.04.1) -- It was already showing that 18.04.1 is installed in the partition that I selected in earlier install (that failed).
[*]Installation completed without any error. System asked to restart to start using Ubnutu installation.
[*]Restarted the system.
[*]On restart, I am shown a new screen (not the original BIOS or Boot options). Refer video [https://www.youtube.com/watch?v=4ZkhsKc29Zg](https://www.youtube.com/watch?v=4ZkhsKc29Zg). This new screen (BIOS kind of screen) have two tabs - "Boot Menu" and "Application Menu". Under Boot Menu tab, only option available is "ubuntu" which is by default selected. On hitting enter, it tries to do something, but within second it comes back to same screen.
[/LIST]


Problem: I am stuck with this new BIOS kind of screen with "ubuntu" as only option and that option does not boot system. I have no option to start the system or enter the original BIOS (which is not even visible anymore). Its kind of very strange that machine's BIOS got updated on installing Ubnutu.

---

### Post by ajgreeny on 2018-12-01
It's difficult to know what the situation is at present with what you've told us so it will be best to see exactly where you are at present

Go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and should help us figure out your problem.

---

### Post by yancek on 2018-12-01
I'm not sure what the problem might be but first, it is significant to let us know which version of windows you are using since microsoft first released windows in 1985.  Members will probably assume you are using the latest (10) version so if not, it is useful to post that info particularly since the advent of UEFI/GPT.

If you do have windows 10, did you read the documentation on the Ubuntu site at the link below on dual booting windows 10 with Ubuntu?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The steps you took all look correct.  Do you remember more specifically what the error on Grub was?
Are you able to boot the Ubuntu install USB?  If so, can you open a terminal and run the following command and post the output:  

> sudo parted -l
Lower case letter L in the command.

Could you post some information on the computer, how old, processor, RAM, etc?.

---

### Post by gauravd-chd on 2018-12-01
Thanks guys for your response.
On doing some research, found out that this issue is specific to Fujitsu laptops, not sure why - but there are some threads where people faced similar issues for Fujitsu laptops dated long back in 2012 too. On Fujitsu laptop Ubuntu install somehow play with BIOS and alters it so that default BIOS screen is not shown and makes the user stuck on that screen with only option of "ubuntu", which too does not work.

See links below to similar issues reported earlier:
Bug filed on Ubuntu in 2015: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1451387](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1451387)
Someone reported in 2014 [https://ubuntuforums.org/showthread.php?t=2257720](https://ubuntuforums.org/showthread.php?t=2257720) -- this thread saved my life. I followed instructions in this to reset the BIOS to factory settings by shorting-circuiting the pins on motherboard. After doing that when I started the laptop and it directly booted Ubuntu. Thank god I found that thread ;-)

---

### Post by timschumi on 2024-04-19
I've recently looked into fixing this issue, and came up with a consistent way of restoring the laptop to full operation.

The boot menu entries can be partially restored by bridging the "CL1_CL2" test point  that is located under or next to the RAM slots.
It may be required to have the laptop powered (or even powered on) while bridging the contacts for the test points to have any effect.
This brings back the  device-based boot menu entries, but does not yet restore access to the  BIOS Setup menu.
For that, a USB stick with [Fujitsu's BIOS update tool]("https://support.ts.fujitsu.com/")  (search by serial number to make sure you find the correct hardware revision) needs to be prepared, booted from, and run.
This restores most BIOS  settings to their default, including the missing BIOS Setup menu.

Alternatively, if the currently installed Linux system is still  bootable, one can use [this tool]("https://github.com/timschumi/ah532-biostools") to restore all entries  without having to go through a BIOS update and reset.
This works by manually  rewriting all broken EFI variables with their expected content.
Please do make note of the list of supported configurations and of the  disclaimer (and let me know in case the tool does or doesn't work on  some previously untested configuration).
In case you want to know more about this works, there is a [post explaining the underlying details]("https://blog.timschumi.net/2024/01/20/ah532-bios-investigation.html").

Lastly, a [workaround for the issue]("https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=f45812cc23fb74bef62d4eb8a69fe7218f4b9f2a") has been merged into the Linux  kernel, which should keep this from occurring on any new  installations.
This patch already ended up in the current installation  media for the Ubuntu 24.04 beta (which I have confirmed to be not affected), and it will presumably be included in  all installation media going forward.

---

