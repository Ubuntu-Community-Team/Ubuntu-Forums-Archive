---
title: "Dell printer drivers, specifically for the 2230d laser printer"
date: 2014-05-22
forum: Hardware
---

### Post by Jonathan_S._Kwiat on 2014-05-22
Greetings, I am pretty much a newbie to Open Source and Ubuntu. I am trying to get my Dell 2230d laser printer to work properly with Ubuntu 14.04 and I am out of my depth. I would appreaciate any help you could give me and let me thank you in advice for spending your valuable time looking at this.

First let me tell you some things I've tried:


[LIST]
[*][[SOLVED] Dell printer drivers, specifically for the 2310d laser printer]("http://ubuntuforums.org/showthread.php?t=1475102")
[/LIST]
  	           	
I am embarssed to say I didn't even notice the difference in model numbers. In any case the solution in this thread almost works for me. I can now print out one document of any length in open office or from firefox although open office gives me the error message "Could not start printer please check your printer configuration" but the print job goes through. However after that any print job stalls with:

"ERROR:
invalidaccess
OFFENDING COMMAND:
copy
STACK
--nostringval--
--nostringval--
--nostringval--
12
-mark-
-mark-
-mark-
"

There do not seem to be any jobs in the printer queue. Turning the printer on and off does not help. Restarting the OS gives me one print job.

Now happily there is a driver for Linux specific to this printer from Dell! 

[Dell 2230d Mono Laser print solution for UNIX]("http://www.dell.com/support/drivers/us/en/prem/DriverDetails/Product/dell-2230d?driverId=K29JP&osCode=HP&fileId=3091569120&languageCode=EN&categoryId=DD")

However that package is in a format that apparently UBUNTU will not accept but there is this tool called [alien]("http://manpages.ubuntu.com/manpages/gutsy/man1/alien.1p.html") that can do the conversion job but:

"        pkg To manipulate packages in the Solaris pkg format (which is really             the SV datastream package format), you will need the Solaris             pkginfo and pkgtrans tools."

And I don't know how to get the Solaris pkginfo and pkgtrans tools or how to merge them with alien if that's how you do it. And I am wondering if I am insane for trying to turn a Solaris UNIX driver into something compatible for UBUNTU because there are comments along the way that you shouldn't do this unless you know what I am doing and I don't know what I am doing.

Needless to say any help would be greatly appreciated for now my desktop is dual boot and Windows 7 has not problems talking to my printer if I need it.

Thank you for your time,

Jonathan Kwiat

---

### Post by Jonathan_S._Kwiat on 2014-08-17
Okay I did want to take the time to answer my own question in case anyone else can benefit from what I learned.

I could not easily build the tools need to enable 'alien' in UBUNTU attempt to transform the Dell Solaris pkg linux driver into a Debian package. However if you wish to attempt that then get the heirloom tools from here:
[https://github.com/halcyon/ubuntu-heirloom](https://github.com/halcyon/ubuntu-heirloom)

Unfortunately this script as written does not install properly on UBUNTU 14.04. For someone experienced in Linux it shouldn't be too hard to make it work but I simply do not want to take the time right now to do this because I have found an acceptable work around. When I learn more about shell scripting I might take another stab at this.

Now I will mention that 'WINE' is worthless as an approach because the driver has to interact with the Linux kernel so you cannot simply download the Windows driver and have it work. I had to learn that myself so I thought I'd mention it.

So the fix I found for this is the virtual machine option. That is using an image of the Windows Operating System you can Install a Virtual Machine on UBUNTU that will allow you to run the whole operating system solely for the sake of being able to use the windows driver and so run your Dell 2230d Laser printer. Amazingly this has worked well for me. I use the VMWare virtual box that is free for individual use but cannot be found in the UBUNTU Software Center. Here is the Link:
[URL="https://my.vmware.com/web/vmware/login"]
https://my.vmware.com/web/vmware/login[/URL]

The virtual machine allows you to share a folder in your home UBUNTU directory. You can install Open Office in the Windows virtual box. Therefore if you need to print anything you just load up the virtual machine, open Open Office, go to your shared folder and print it out from inside the virtual machine and you Windows Driver will be able to handle the file. I find this kind of crazy but it works very well, and doesn't require me to spend hours debugging some scripts that may or may not give the tool to get a linux driver to work for this printer.

I would say that the one thing that may stymie you is the need for a Windows Installation Disk. Technically VMware says certain kinds of hard-disks can allow you to run the image on the partition should you have a dual boot computer. My Dell did not ship with an installation disk. Technically I believe you can ask Dell for one. But there are others ways but I will not mention them because they are in gray areas of the law. Just remember you did pay for this OS and don't go crazy trying to get a live iso off the backup partition. Just call Dell or do something else. In any case you will need your Windows Product key and so you may find this link useful:

[http://www.pcworld.com/article/246040/how_to_find_your_windows_or_office_product_key.html](http://www.pcworld.com/article/246040/how_to_find_your_windows_or_office_product_key.html)

It is strange I bought a [Canon MX922]("http://www.usa.canon.com/cusa/consumer/products/printers_multifunction/office_all_in_one_inkjet_printers/pixma_mx922") without thinking about it because it is top rated product for it's class and I ran into the same exact problem. I could not get the scanner driver to work so any of the Linux software for scanners would recognize the device. But this same approach works. What's could about it is my machine is fast enough, and my day to day demand are low enough that running a virtual box does not really slow my machine. I can keep the virtual machine running and only tab over to it when I have to print something and that's almost as fast as having everything running in UBUNTU native.

I feel this is an ugly solution, and I wish I was good enough that I could easily do something better but I can't right now. I hope this helps someone besides myself. 

May you be well,

Lathian

---

### Post by pdc on 2014-08-18
> I bought a Canon MX922 without thinking about it because it is top rated product for it's class and I ran into the same exact problem. I could not get the scanner driver to work

Hi Jonathon; sorry to hear you couldn't get the scanner working immediately:

Canon provide a programme called **[COLOR="#0000FF"]ScanGearMP[/COLOR]** to run the scanner, and a linux scanner driver for your machine: in a debian package: [http://support-asia.canon-asia.com/contents/ASIA/EN/0100518302.html#r=s&r=s](http://support-asia.canon-asia.com/contents/ASIA/EN/0100518302.html#r=s&r=s)

(they also provide an rpm package and the source code...............)

If you click to download; and select **SAVE**: you download [COLOR="#008000"]scangearmp-mx920series-2.10-1-deb.tar.gz
[/COLOR]
commands; line by line in a terminal are: (hitting the ENTER key after each paste ...)

[COLOR="#FF0000"]cd Downloads
tar -zxvf scangearmp-mx920series-2.10-1-deb.tar.gz
cd scangearmp-mx920series-2.10-1-deb
./install.sh [/COLOR]

and you will be asked for your sudo password

to run **[COLOR="#0000FF"]ScanGearMP[/COLOR]** initially the terminal command is **> [COLOR="#FF0000"]scangearmp[/COLOR]**

..............thereafter, one creates a launcher ........................

---

### Post by Jonathan_S._Kwiat on 2014-09-05
Just wanted to confirm that ScanGearMP does work for me. And the cannon model does work with UNIX with no problems. Thanks for the reply.

---

