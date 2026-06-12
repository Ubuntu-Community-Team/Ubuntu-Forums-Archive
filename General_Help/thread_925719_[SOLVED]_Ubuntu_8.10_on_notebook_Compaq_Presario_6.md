---
title: "[SOLVED] Ubuntu 8.10 on notebook Compaq Presario 6210?"
date: 2008-09-20
forum: General Help
---

### Post by lovinglinux on 2008-09-20
I'm running Ubuntu Hardy on my machine for a month and I'm very pleased with it.

The thing is that I also would like to install Ubuntu on a notebook Compaq Presario 6210, but there are some issues with this model that prevents installing Ubuntu Gusty/Hardy or other distros with the same kernel versions.

The notebook came with Mandriva Linux 2007 and I replaced it with Windows XP about a year ago (yeah, I know..). Mandriva 2007 rescue CD install without issues, but I can't update it and I really prefer Ubuntu. The only solution is to flash the BIOS, but I really don't want to do that. 

So, I was wondering if I will be able to install Ubuntu Intrepid on this notebook?

---

### Post by lovinglinux on 2008-11-09
I'm still running Hardy on my Desktop and, for now, upgrading doesn't feel very appealing to me. Nevertheless, thanks to Intrepid, I was able to install Ubuntu on a HP V6000 series notebook and finally get rid of Windows.

My notebook has some serious issues related to a BIOS bug and even after flashing it with a new BIOS I was able to install other Ubuntu releases. I tried 6.06, 7.10, 8.04, 8.10rc1, 8.10, Linux Mint, Mandriva 2008 and Mandriva 2009. Also tried Wubi, Unetbootin and burned dozens of DVD's, but every time I tried to install Linux on that machine I got some sort of errors. Sometimes I couldn't even run the Live CD form a disc or hard drive.

So two days ago I decided to give Intrepid another chance and tried to install it on the notebook. The Live CD run well the first time, but when trying to install I got an "I/O buffer error on device sr0". Certainly not an Intrepid issue, because this error was the major problem I have found with other releases or distros. I guess is a DVD error. So instead of burning the DVD at the lowest speed as usual, I decided to burn it at maximum speed this time. Then I shrunk the Windows partition and created some space for Ubuntu and started the installation process.

In the first attempt with the DVD recorded at maximum speed, the installation stalled when you choose the system language. Despite the fact that I was able to start the installation process of Intrepid before, it never went further than the step 3 of the process. So I tried to install without changing the default English option. For the first time I was able to reach the partitioning step and create the necessary partitions, but when the partitioner actually started to format the disc I got another error and the installation process returned to the step when you choose the partitions. So I decided to boot into Windows again and created the necessary ext3 partitions with PartitionMagic. Then inserted the Intrepid disc again and the installation went pretty well.

After install, I get a few glitches and errors, but nothing serious enough to consider going back to Windows. Even the wireless was working with the restricted drivers installed from the repositories. 

I have already deleted the Windows partition. So, bye bye Bill.

---

