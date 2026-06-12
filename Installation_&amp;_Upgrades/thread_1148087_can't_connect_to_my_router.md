---
title: "can't connect to my router"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by cmar87 on 2009-05-04
Hello,

I'm a new user to the Linux Ubuntu OS, and I am new to this forum. Have never been here, this is my first thread I will read and create.

Recently I have installed Ubuntu on a partition on my primary HDD that also contains my main Windows OS.

Need help wireless connecting my Ubuntu, to my Linksys WRT54G wireless router. I have tried opening the network options, to create my wireless network with information located on the router's homepage '192.168.1.1'. However this was unsuccessful, and I have also tried various commands and instructions with no results.

My problem seems to be in these instructions:

"If you have access to the Internet, you can see if your wireless cards is in the list of cards supported by ndiswrapper on the ndiswrapper website.

To install ndiswrapper, install the package ndiswrapper-utils (see Add Applications). This package is provided on the Ubuntu CD. If you have access to the Internet, you can also optionally install a graphical tool, ndisgtk from the Universe repository (see ../../add-applications/C/#extra-repositories).

In order to set up ndiswrapper, it is necessary to obtain the Windows driver for your wireless card. Generally, the best way to do this is from the CD supplied with your wireless card. You should copy two files to the same place on your computer, one ending in .SYS and one ending in .INF. If you find any files which end in .BIN, also copy those. If you are not able to find the right files, and have alternative access to the Internet, you may be able to obtain help from the ndiswrapper website.

If you have installed the graphical tool ndisgtk, to set up ndiswrapper, simply select System &#8594; Administration &#8594; Windows Wireless Drivers from the menu, and follow the instructions given.

If you have not installed the graphical tool, use this procedure:

   1.

      Open Applications &#8594; Accessories &#8594; Terminal and type:

      sudo ndiswrapper -i ~/Desktop/drivername.inf

      [Note]    

      The above command assumes that your .INF file is named drivername.inf and was copied to your Desktop. Replace these values if necessary.
   2.

      To check if it is working correctly, type:

      ndiswrapper -l

      If it is working correctly, you should see:

      Installed ndis drivers:
              {name of driver}  driver present, hardware present

   3.

      For ndiswrapper to function, you need to load a module. To do this, type:

              sudo depmod -a
              sudo modprobe ndiswrapper

   4.

      To ensure that the module is loaded each time you boot the computer, type:

      sudo ndiswrapper -m
"

Just to note, in the recent months I seem to have a lack in capacity of problem solving abilities due to bad weather and stress, so please explain everything simplistically and step-by-step. Hope I'm not asking for too much, but I really need help to solve this issue. I have a feeling my answers are right here infront of my, but since I am unexperienced with Linux, I would really appreciate a step-by-step guide.

So far I understand that I must install 'ndisgtk' and 'ndiswrapper'. Thanks in advance.

---

