---
title: "Belkin... I am desperate for help please..."
date: 2006-03-17
forum: Hardware &amp; Laptops
---

### Post by Scottya on 2006-03-17
Ok, heres my story.

I have just succesfully installed Ubuntu! Yay! The installation went great. All my partitions are fine, and its all good!

But, I am having to post this in XP. This is because Ubuntu doesnt seem to want to connect to my wireless router from the Belkin Wireless G USB Network Adapter in my computer.

This is fustrating, as you could imagine.

If anybody knows of a way I may be able to get round this problem and get my Ubuntu connected to the internet, please say!

Thanks everyone.

---

### Post by navilon on 2006-03-17
Give this a try
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

---

### Post by Scottya on 2006-03-17
Ok I had a look at it, but I dont get why you sent me to it :S

I dont get how that will help me, could you possible instruct me how to use it?

Thanks navilon!

---

### Post by roachk71 on 2006-03-17
[LEFT]Hi,

First, what model and version are you using exactly? I'll check with the compatibility list on the NDiswrapper site (note that ndiswrapper does support many chipsets, but not all just yet; it's under constant development.)

My own card (F5D7010, version 5, cardbus) isn't correctly supported by the included ath_pci driver, so I had to download the kernel tree and development tools, then recompile the kernel and build the ndiswrapper source myself. I had completely ditched XP, and this problem had me biting my nails and pulling hair!

Also, what CPU architecture is your computer using? This is very important.

Unfortunately, there really is no simple solution, but there is at least one that works.
[/LEFT]

---

### Post by Scottya on 2006-03-17
Well the Info I have on the stick itself is:

802.11g - 54mgps -- This is the Dixons page for it:
[http://www.dixons.co.uk/martprd/store/dix_page.jsp?BV_SessionID=@@@@2066440940.1142622494@@@@&BV_EngineID=ccddaddhfhkldelcflgceggdhhmdgmj.0&page=Product&sku=369188&fm=1&sm=2&tm=0]("http://www.dixons.co.uk/martprd/store/dix_page.jsp?BV_SessionID=@@@@2066440940.1142622494@@@@&BV_EngineID=ccddaddhfhkldelcflgceggdhhmdgmj.0&page=Product&sku=369188&fm=1&sm=2&tm=0")

I hope this helps.

And I dont quite understand what you mean by CPU architecture.

Thanks for your help.

---

### Post by roachk71 on 2006-03-17
[LEFT]What I mean is, are you running a Pentuim, PowerPC or Athlon/Duron?

Ah... And another place you might need to check first, in case it is supported, is in the network configuration dialog for device ath0. If that device is shown, try setting that up first, with the ESSID and key from the router, and enabling the connection. If the connection is still iffy (that's how it went for me,) the ndiswrapper module from their site may have to be built from source.

Of course, you'll have to follow the kernel compilation directions in the Kernel Compilation for Newbies link in my signature before building the ndiswrapper source, since it'll need pre-built interface modules for compilation.

You can find this dialog under System->Administration->Networking.
[/LEFT]

---

### Post by Scottya on 2006-03-17
Oh I see... Its Pentium.

In the installation, it didnt pick up the USB Adaptor at all... So I dont know if that is significant.

Basically... do you know of a way I can get my internet running in Ubuntu, in idioits terms hehe :) Im kinda new to all this stuff.

---

### Post by Scottya on 2006-03-17
Sorry for the double post, but here is another link to the product:

[http://catalog.belkin.com/IWCatProductPage.process?Merchant_Id=&Section_Id=201576&pcount=&Product_Id=203472&Section.Section_Path=%2FRoot%2FNetworking%2FWirelessNetworking%2F80211gWi%2E%2E%2Etworking%2F](http://catalog.belkin.com/IWCatProductPage.process?Merchant_Id=&Section_Id=201576&pcount=&Product_Id=203472&Section.Section_Path=%2FRoot%2FNetworking%2FWirelessNetworking%2F80211gWi%2E%2E%2Etworking%2F)

And also, it is shown here: [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

---

### Post by roachk71 on 2006-03-17
First, make sure you've rebooted into your fresh Ubuntu system, and, once at the desktop, insert your Ubuntu Install CD. It will be needed shortly.

1. Go to System->Administration->Synaptic Package Manager,
2. Click the search button at the top right of the window, and search for ndiswrapper,
3. Click on the checkbox to the left of ndiswrapper and select "Mark for installation"
4. Click Apply. A dialog will appear to confirm.

For the next steps you need to install and use the windows version of 7-Zip (google for this) to unpack the InstallShield cabinet and search it for the driver folder, then burn the entire folder to CD. The Linux unshield utility can't deal with the new format.

Once you reboot into linux, insert the new driver CD.

(I should note here that I couldn't find any reference to this wireless card in the compatibility list. So it may or may not work in Ubuntu either way... We'll just have to see; there are many USB-based NICs that don't.)

If you haven't changed the behavior yet, a file manager window will pop up. Note the location of your driver folder, and open it, looking for an .inf file for your card. In my case, it's BLKWGN.inf; yours is likely different. Then close the window.

Next, open a terminal window (yes, I know those new to Linux don't like the idea, but there are many times you can't get around using it.)

 
Type in the terminal: ndiswrapper -i /media/cdrom/{driver's folder}/
{name of the .inf file}.inf

Be sure to type the driver filename exactly as it appears, since the terminal is case-sensitive.

Now, type in:
```

ndiswrapper -l

``` 
The response should read:

{driver name}  driver present,hardware present

If it does not, the device is probably not supported in this version of ndiswrapper. The latest version from the developers is 1.10; the included version is 1.1. Linux versioning schemes are different.

If it is, use this command:
```

modprobe ndiswrapper

``` 
To make this device start up at boot, one more step has to be followed. type
```

sudo gedit /etc/modules

``` 
and after the reference to the mouse device, insert ndiswrapper, save and exit. Then close the terminal window.

Then reboot back into Ubuntu.

Now, you'll have to open the Networking dialog again, and set up device wlan0 for your network, with the router's ESSID and encryption key. Set the device as active, then close the Networking dialog, and reboot again.

Everything should be up and running at this point.

---

### Post by roachk71 on 2006-03-17
[LEFT]If the architecture is Pentium, the default running kernel should be fine for now.

The reference is important for building a custom kernel for the latest ndiswrapper version, which, if the previous directions didn't work, you might have to follow, temporarily using a wired LAN connection.

Also, if your PC has more than 896MB of RAM, the 686 kernel is necessary to use the extra memory, and if it's a full Pentium 4, the 686-smp kernel is needed to take full advantage of the P4's hyperthreading (this speeds the system up considerably.) Athlon/Duron users should download the K7 kernel.

After the tools and all of the sources are downloaded and installed you won't need the LAN connection, and it can be disabled unless something goes wrong during the builds.

During the build process, the compiler will optimise the resulting code for the computer's architecture.

A side note: Once you've built your kernel for the first time, the sense of accomplishment makes this practice addictive. It's no wonder dedicated Gentoo users won't give their distro up!

All I can say is, if you really like Linux and want to keep it, don't be afraid to "get your hands dirty." <grin>
[/LEFT]

---

### Post by Scottya on 2006-03-17
Ok thanks!

Nice to see Linux make life easy -.- lol... Will I be able to burn those files onto a DVD instead?

I have no CD's.

And I downloaded 7-zip.... its an exe file :S

Or... alternatively... is there a NIC that is compatable with a Belkin Wireless Router in Ubuntu and XP?

Cause I would preferably just go and buy that to be honest.

---

### Post by roachk71 on 2006-03-17
[LEFT]Have you executed that .exe file from Windows yet? That's 7-Zip's installer.

Once you do, you can access the 7-Zip File Manager from your Windows Start menu.

And Yes, you should be able to burn those onto a DVD-R/W or DVD-R and access that volume from Ubuntu like a CD... The icon should appear on your desktop, and disappear once it's ejected.

You'll really like 7-Zip: it handles many compression formats, and its LZMA compression algorithm is better than the standard ZIP used by Windows! :cool:

There are a few NICs which are entirely compatible; I'll look in the Ubuntu HCL to find the best recommendation. Be back in a few...
[/LEFT]

---

### Post by Scottya on 2006-03-17
Thanks man.

Ok I have installed 7-Zip and I like it :D

Now what do I do... btw... do you have msn? It may make it a bit easier for us to communicate.

Thanks.

---

### Post by roachk71 on 2006-03-17
[LEFT]No, but I have Yahoo! Messenger (using Gaim). Here's a link to quite a few wireless cards:

[http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)

There are still quite a few USB network adapters which simply don't work in Ubuntu. You might want to invest in one of the PCI (or, if you're a notebook user, PCMCIA or Cardbus) cards; the support is much better for those.

If you use Yahoo! Messenger, there should be a Y! icon somewhere next to my avatar. If not, it will be shortly.
[/LEFT]

---

### Post by Scottya on 2006-03-18
Ok... The model number for my adapter is F5D7050 ...

So, according to the list it should work :O

But... I done all the stuff you said, and it finds the .inf file... but when I type ndiswrapper -l ... it doesnt find the device.

---

### Post by roachk71 on 2006-03-18
[LEFT]Here's something i picked up from the ndiswrapper Wiki:
```
[LIST=1]
[*]Card: Belkin F5D7050 (USB 2.0 Adaptor 802.11g 54Mbps)[LIST]
[*]Chipset: Conexant (PrismUSB)
[*]usbid: 050D:7050
[*]Driver: Install the drivers for windows included in the box and fetch the .inf and .sys fyles from the installation directory.
[*]Other: linux-2.6.9: Blocks Linux momentarily when another device is plugged into the same USB Hub, more precisely a 1.1 memory stick.
[*]Other: SuSE 9.1, kernel-2.6.8-default (kernel-of-the-day 22 Dec. 2004): 1.0rc1 with bknUSB.inf from the vendor CD and WEP security works quite stable. The procedure as described in WiKi/SuSE 9.1. Professional.
[*]Other: SuSE 9.1, kernel-2.6.x-smp: doesn't work, 'modprobe ndiswrapper' freezes the system.[/LIST] [/LIST]
``` 
Unfortunately, you'll have to reboot into Windows and find the installation directory... Belkin is much like a certain other company we all know and distrust; they don't want the user to use anything but Windows.

I wish I could be of more help in this regard, but I don't have a Windows machine; Mine is all Ubuntu.

And a special note: The F5D7050uk model isn't specifically listed, although a comparable USB model is. These may or may not be the same.

If you have access to another internet-connected PC, I could walk you through the other steps (kernel compilation and installation, installing the latest ndiswrapper, etc. Since you won't be able to simply dual-boot between Linux and Windows during the process. I just had to resolve a circular DNS issue on my end, so my messenger connection should be more reliable. I'm keeping my ears on with Yahoo Messenger, so you can IM me.
[/LEFT]

---

### Post by roachk71 on 2006-03-19
[LEFT]Hmmm...

Looks like IM is out, at least with the Unix version of Yahoo! Messenger; it tends to use too much CPU, and both IM programs disconnect randomly. :mad:
[/LEFT]

---

### Post by Scree on 2006-03-19
I'm having wireless issues as well.
This is what I was able to glean from this thread:
one- Wireless compatability isn't directly coded into the system
two- I have to activate it through the third tab to the right (the name escapes me at the moment)
three- I have to enter code
Currently, my head is spinning at this since I'm extremely new to this OS (but determined to learn it). 
Feel free to dumb down the explanation as much as possible.
creative liberties, ahoy.

---

### Post by Scottya on 2006-03-19
Well... yes I do have another PC with internet connection, but I also have my PSP which is connected to the wireless network.

But, the other PC does not work with Yahoo! Messenger for some reason, and I can only get MSN with the PSP.

When you said that some wireless network cards are directly compatable with Ubuntu and XP, could you please specify more on wether I just have to plug it in, or if I need to mess around in Terminals more hehe.

Thanks.

---

### Post by Scottya on 2006-03-19
OK I came accross this website:

[http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)

After looking around I have found out that I need the rt2570 Driver to work my F5D7050 (Belkin Wireless USB Adapter)

But I havent got a clue in the world how to work the diver.

Please, can anyone just give me an idiots guide in English every day language on how to get my internet adapter working with Ubuntu.

If not, another wireless USB or Network card that is directly compatable with Ubuntu and XP.

Thanks.

---

### Post by Scottya on 2006-03-20
Bump

---

### Post by Scottya on 2006-03-20
Sorry for the constant bumping, this is a really big problem for me though.

I am desperat to get this working!

---

### Post by roachk71 on 2006-03-20
[LEFT]I have a new MSN Messenger account; you can try IM'ing me by clicking the butterfly now. :cool:

Hopefully there won't be a random disconnect with this account.
[/LEFT]

---

### Post by Scottya on 2006-03-20
Great OK, Thanks!

---

