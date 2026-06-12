---
title: "My computer won't start up anymore. What can I do?"
date: 2016-06-05
forum: Hardware
---

### Post by jdkcarlson on 2016-06-05
Hi all, I have an Acer Aspire R5-471T notebook which seems very reticent to work with Ubuntu 14.04. It crashes or freezes with some frequency and on restarting drivers seem to be missing (for example, I keep losing wireless). Sometimes the computer apparently freezes but the mouse pointer remains mobile (but unable to click) anything. Reading advice online intended to fix this, and not wanting to restart and lose more drivers, I tried to fix the problem from tty1. I was able to restart gdm (I can't use lightdm anymore either for some reason) according to the terminal feedback, but it didn't appear in tty7.

Something I read online suggested the problem might have been nvidia drivers, but I suspect following this suggestion made things worse. When I eventually sudo rebooted, the normal login happened, but after the dots I found a black screen. I'm able to get to a terminal via the following workaround: [LIST]
[*]restart in recovery mode
[*]resume regular boot
[*]accept the error "*Starting ACPI daemon initctl: 
Event failed" which occurs in tty1
[*]log in to terminal there.
[/LIST]
I've tried purging nvidia and doing apt-get install nvidia-352 but I have the same problems. I see there are several versions of NVIDIA flies but don't know which are relevant. So I don't even know if this is really the problem. What can I do?

---

### Post by RobGoss on 2016-06-05
Have you try a lighter version of Ubuntu they may work better on that Netbook like[ Lubuntu]("http://lubuntu.net/") or[ kubuntu]("http://kubuntu.org/"), there lighter and use less resources. I'm not sure what your specs are but from what you are describing 14.04 may not be the best choice. I'm currently running [Ubuntu Mate 16.04]("https://ubuntu-mate.org/download/")  on my HP mini Netbook with out any problems I did have Ubuntu 16.04 installed as well and it preformed just fine....

I think one of the best things about Ubuntu is the fact that we have a number of distributions we can try

---

### Post by jdkcarlson on 2016-06-05
Hi Rob, I believe what I have is a "notebook" and not a "netbook." Here are the specs (although I seem to have a 512GB hard drive, not the 256): [http://www.ultrabookreview.com/9304-acer-aspire-r14-review-2/]("http://www.ultrabookreview.com/9304-acer-aspire-r14-review-2/"). I consulted with a more computery friend when I bought it and was assured it was really much more than I needed in terms of specs than what I really needed (I mostly read documents, write in LaTex, browse the internet, and occasionally watch something on Netflix), but my family badgered me into getting a "nice" computer they thought would last longer.

And after all, I did manage to run Ubuntu on this computer for about four months, so I don't think it's that the build is too heavy. But I don't know why lightdm has stopped working and now I can't log in at all. I'm also not really confident in my ability to change versions of Ubuntu from the command line when I'm apparently now too stupid to even start up the GUI. Some people have also advised I upgrade to 16.04 but other people have suggested doing so might break some of the few things I do still have working. 

Would you happen to have any suggestions of things I can do to figure out what is wrong and become able to log in again to a version of Ubuntu I have some (albeit limited) understanding of without installing another distribution?

---

### Post by RobGoss on 2016-06-05
So this is a new installation of 14.04 correct? and is this machine only running Ubuntu 14.04 and not a dual boot?

If it were me I would load up another** ISO **file using [Pendrive]("http://www.pendrivelinux.com/") on a** USB **drive of **14.04** or **16.04** and try installing it again this time when given the options check the two option to install **updates** and **third party **application. I also think it would be a good idea to go with **16.04** seeing you have so much trouble with 14.04..... I would 

The link you posted with your specs seems more them enough to handle Ubuntu

---

### Post by jdkcarlson on 2016-06-05
This installation was new as of January when I installed 14.04 off a stick because my friend said it was more stable and better supported at present. I keep a small  partition with Windows 10 still on it which I boot into from time to time to download packages or drivers manually when the wireless stops working on Ubuntu (which has happened with some regularity).

Would this reinstallation kill my existing files? I have many files which live only on this Ubuntu partition at present.

---

### Post by RobGoss on 2016-06-05
> **jdkcarlson said:**
> This installation was new as of January when I installed 14.04 off a stick because my friend said it was more stable and better supported at present. I keep a small  partition with Windows 10 still on it which I boot into from time to time to download packages or drivers manually when the wireless stops working on Ubuntu (which has happened with some regularity).

Would this reinstallation kill my existing files? I have many files which live only on this Ubuntu partition at present.


> Would this reinstallation kill my existing files? I have many files which live only on this Ubuntu partition at present.

Yes it would remove everything from the Ubuntu partition and reinstall everything again. You can backup any important file you wish to keep

**NOTE: **If this is something you really don't want to do them leave everything as it is and maybe we can try to figure out what's going on with your currently installation

---

### Post by jeremy31 on 2016-06-05
Do a backup for any files you want to keep, put them on a flash drive or something to save them

---

### Post by RobGoss on 2016-06-05
Let me make sure I understand what's going on with your installation, You loose your **WiFi** connection and you can't **login** to your system correct?

---

### Post by jdkcarlson on 2016-06-05
I'd rather not have to back up 450 GB of files to install a new OS which I also have no guarantee will work. It tool me many hours to get the first installation to work even as well as it did. 

For instance I had to change BIOS to even get the trackpad to work. 

This computer crashes all the time and when it does driver files seem to be moved or destroyed and I lose functionality. I've remade backports at least four times because that's the only way wifi works and those files keep getting killed. I also one day found I couldn't log into lightdm any more no matter what I did, and now I can't log in at all, possibly due to screwing up NVIDIA drivers. I've got about a dozen smaller behaviors that are wrong or bad I don't know how to fix, but th is are the big ones. 

I'd rather not have to delete all my files. I can't believe my system wants this badly not to work.

---

### Post by RobGoss on 2016-06-05
Are you able to boot up to the login screen

If you can boot up to your login screen this post maybe able to help you gain access [http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)

---

### Post by jdkcarlson on 2016-06-05
Not if you mean the screen with a background and a window to type username and password. 


If I ignore Grub, then the red background appears, then the Ubuntu dots, and after that a blank black screen forever. I am able to get to a terminal, but only through the workaround I described a few posts up in this thread. I can log in to this terminal after initctl fails, but I don't know if this is what you mean by a login screen.

---

### Post by RobGoss on 2016-06-05
> **jdkcarlson said:**
> Not if you mean the screen with a background and a window to type username and password. 


If I ignore Grub, then the red background appears, then the Ubuntu dots, and after that a blank black screen forever. I am able to get to a terminal, but only through the workaround I described a few posts up in this thread. I can log in to this terminal after initctl fails, but I don't know if this is what you mean by a login screen.

> [COLOR=#000000]Not if you mean the screen with a background and a window to type username and password[/COLOR]

Yes the login screen I mean

---

### Post by oldfred on 2016-06-05
Link shows a Skylake Intel chip?

I built new SFF system with Skylake i6500 and knew I needed the very newest kernel, support software & drivers. So even though 16.04 had not then been released, that is what I installed. No issues, but not a laptop.

But I suggest downloading 16.04 and run it in live mode and see how it works.
Did you install in UEFI or BIOS boot mode?

---

### Post by RobGoss on 2016-06-05
> **oldfred said:**
> Link shows a Skylake Intel chip?

I built new SFF system with Skylake i6500 and knew I needed the very newest kernel, support software & drivers. So even though 16.04 had not then been released, that is what I installed. No issues, but not a laptop.

But I suggest downloading 16.04 and run it in live mode and see how it works.
Did you install in UEFI or BIOS boot mode?


> [COLOR=#000000]But I suggest downloading 16.04 and run it in live mode and see how it works.[/COLOR]

Hello Fred, I think his concern is all the files he has on 14.04 that's installed would he be able to access them to back them up on maybe a USB drive

---

### Post by jdkcarlson on 2016-06-05
Rob, in that case, yeah, I can't make it to login. I boot in recovery mode, continue regular boot, and hit return after an error to get a terminal. I'm sorry I missed your question earlier about login loop. I had indeed seen that page earlier when I couldn't boot into lightdm and went through almost all of the suggestions without regaining functionality (the rest, I didn't have the knowledge to implement). I meant to start a post about that sometime but then things got worse.

You're right that I don't know how to transfer all my files off out of terminal, just the GUI. If I do resort to that, I'd like help doing that. I can't afford to lose this data. I did get a new external HD recently to try to deal with this and other eventualities but I don't know how to work solely out of the terminal for much yet because I used to have a GUI.

Fred, I'm not sure, but when I do "ls /sys/firmware/efi" I get a nonempty list, which other sources on the net say means I am using UEFI. If there's another way you'd like me to check, please let me know.

lspci shows I do indeed have a Sky Lake Host Bridge. I don't know what this means, but it was running on 14.04 all the way through to yesterday.

Can I tell you something from dmesg or some other config file, maybe?

---

### Post by oldfred on 2016-06-06
I downloaded inxi and ran it. 
       oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)

If at terminal, this shows UEFI boot options:
sudo efibootmgr -v

If you can boot 16.04 live installer, then you will have a gui.
Did you partition (hopefully gpt) and format partitions on the new drive yet. If not that would have to be done also.

---

### Post by jdkcarlson on 2016-06-06
Fred, I downloaded and ran inxi but am not sure what you wanted me to report back. It shows CPU as a dual-core Intel Core i7-6500U CPU though if that helps.

I also did sudo efibootmgr -v but don't know how to interpret the output it has Boot0000 through Boot0007 and Boot2001 through Boot2003. These look a bit like the grub options. The names are, in that order

Unknown Device
Unknown Device
Windows Boot Manager
ubuntushimx64efi
ubuntugrubx64
ubuntuMokManagerEFI
EFI USB Device
EFI DVD/CDROM
EFI Network

Appellations like HD, ACPI, and RC appear next to them. 

I haven't even taken the new drive out of the box yet, but I believe it's formatted NTFS since they assume most users have Windows.

I'm not sure what you mean exactly here about the live installer. Are you suggesting I run an OS off a stick to experience GUI again and verify that it works, or that I copy all my files to this new HD, once it's partitioned and reformatted, and then install 16.04 in the partition where 14.04 currently lives?

---

### Post by oldfred on 2016-06-06
I was suggesting testing 16.04 from live installer, just to see if it works or works better.
Then you may have more confidence that installing it works.

Is new drive just for backup, or are you planning on converting to it as main drive?
Or installing 16.04 directly to it?

I do like to have a current version of Ubuntu on every drive, even if a small partition for emergency boot on data drives.

---

### Post by jdkcarlson on 2016-06-06
Fred, good plan. The new drive is a 2TB external. Could I remove it and install it in the computer itself, you mean? 

I was planning on using it to sort all the miscellaneous files and photos I saved from my old, recently deceased Mac drive, along with partial ddrescue and so forth that have resulted from my salvage efforts. I had enough space for all of it, but not enough to move it, if that makes sense.

The idea to have a bootable copy of Ubuntu on every drive makes a good deal of sense to me.

---

### Post by oldfred on 2016-06-06
It is just with UEFI and Ubuntu's grub it is not as easy as BIOS boot is/was.
But I prefer gpt and since my new hardware is UEFI, do configure new drives as UEFI boot. 
But that requires gpt with and ESP - efi system partition for UEFI boot and bios_grub in case configuring for BIOS boot.

And your Acer has a unique requirement of enabling a Supervisory password and setting "trust" on grub's efi boot files for internal boot drives.
I think all external drives only boot from /EFI/Boot/bootx64.efi and internal drives can use that as a fallback or hard drive entry in UEFI for booting.
Grub will not install to any ESP other than the one on the drive seen as sda. Then you have to manually copy files from sda's ESP to sdb's ESP.

---

### Post by jdkcarlson on 2016-06-16
Okay, I successfully backed up my /home with rsync, verified using the option -nviacz that everything was transferred correctly, and then discovered it was possible to install 16.04 retaining the home folder so the caution wasn't really necessary. This installation starts and lightdm started running after I chown'ed .Xauthority, so I'm going to mark this as solved now. Thank you for all the help.

---

### Post by kurt18947 on 2016-06-16
If I'm understanding this thread correctly, the caution of backing up difficult  or  impossible to replace data files is ABSOLUTELY necessary. No matter how well a machine is running, it could be a scrambled, encrypted (not by you) or a non-functioning pile of plastic, copper and silicon upon its next start. I'm glad 16.04 appears to have fixed your issues. You have a machine with the newest hardware (looks great by the way) which usually works best the the newest O.S. Linux is often a little behind Windows & OSX in their hardware support due to lukewarm interest by hardware manufacturers in supporting Linux, it's not a priority for them on desktop machines.

---

### Post by jdkcarlson on 2016-07-21
Thanks, kurt. Yes, the login problems are solved for now aside from a residual "login keychain" alert despite the fact that I don't have to type a password to log in to the system itself (?). Unfortunately, I managed to deactivate the trackpad and haven't been able to get it back, and the keyboard often spontaneously quits as well. This computer does have good specs, but as a more Linux-savvy friend keeps telling me, it just wasn't meant to run Ubuntu. :/

---

