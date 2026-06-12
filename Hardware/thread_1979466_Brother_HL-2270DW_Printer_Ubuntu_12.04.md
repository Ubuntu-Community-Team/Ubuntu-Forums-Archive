---
title: "Brother HL-2270DW Printer Ubuntu 12.04"
date: 2012-05-13
forum: Hardware
---

### Post by willejos on 2012-05-13
Just thought I'd post this here since there are a few threads with people having trouble installing this printer and the [SOLVED] ones are using 11.04.. I tried following suggestions from [this thread]("http://ubuntuforums.org/showthread.php?t=1842880&highlight=2270dw"), [this thread]("http://ubuntuforums.org/showthread.php?t=1757153&page=2&highlight=2270dw"), and [this blog post]("http://chadchenault.blogspot.com/2011/09/brother-hl-2270dw-printer-driver.html") but couldn't get it to work in 12.04 (printer showed in cups but just hung, didn't print). I also use arch linux and the install script I use for arch also worked for me on 12.04. I connect through usb though I imagine connecting over the network would work by changing he device URI in /etc/cups/pritners.conf to use an IP address as mentioned in the above threads.

```

#!/bin/bash
# Brother HL-2270DW printer install tested on arch and ubuntu 12.04
# https://bbs.archlinux.org/viewtopic.php?id=109570
# https://bugs.gentoo.org/show_bug.cgi?id=285166#c12
# http://github.com/willejos/bash

[[ $UID -ne 0 ]] && echo "Must run as root" && exit 1

which bsdtar > /dev/null
if [ $? == 1 ]; then
  echo "you need to install bsdtar before running this script"
  exit 1;
fi

which perl > /dev/null
if [ $? == 1 ]; then
  echo "you need to install perl before running this script"
  exit 1;
fi

echo -e "\nMake sure cups is running before proceeding...\n"
read -p "Hit any button to continue." -n 1

echo -e "\n\nWhere's your init script directory?"
echo -e "1. /etc/init.d/\n2. /etc/rc.d/"
read -p "(Select 1 or 2): " INIT_DIR
while [[ $INIT_DIR != 1 && $INIT_DIR != 2 ]]; do
  read -p "Where's your init script directory? (choose 1 or 2): " INIT_DIR
done

START_DIR=$(pwd)
mkdir br_tmp && cd br_tmp
wget http://www.brother.com/pub/bsc/linux/dlf/hl2270dwlpr-2.1.0-1.i386.rpm
wget http://www.brother.com/pub/bsc/linux/dlf/cupswrapperHL2270DW-2.0.4-2.i386.rpm

if [[ ! -f hl2270dwlpr-2.1.0-1.i386.rpm || ! -f cupswrapperHL2270DW-2.0.4-2.i386.rpm ]]; then
  echo -e "One or both files not found: \n  hl2270dwlpr-2.1.0-1.i386.rpm \n  cupswrapperHL2270DW-2.0.4-2.i386.rpm \n\n Was there a problem with the download?"
  exit 1;
fi

# extract and check directories exist
bsdtar -xf hl2270dwlpr-2.1.0-1.i386.rpm
bsdtar -xf cupswrapperHL2270DW-2.0.4-2.i386.rpm
HL_DIR=""$START_DIR"/br_tmp/usr/local/Brother/Printer/HL2270DW/inf/"
CUPS_DIR=""$START_DIR"/br_tmp/usr/local/Brother/Printer/HL2270DW/cupswrapper/"
if [[ ! -d "$HL_DIR" || ! -d "$CUPS_DIR" ]]; then
  echo "rpm extraction failed"
  exit 1
fi

# in-place edit files
cd "$HL_DIR"
perl -pi -e 's/printcap.local/printcap/g' setupPrintcap2
if [ "$INIT_DIR" == "2" ]; then
  cd "$CUPS_DIR"
  perl -pi -e 's/init.d/rc.d/g' cupswrapperHL2270DW-2.0.4
fi

# copy files to system and install cupswrapper
cd "$START_DIR"/br_tmp/
cp -ri usr/* /usr/
cp -ri var/* /var/
cd ../ && rm -rf br_tmp

echo -e "If I hang here, be patient....\n"
/usr/local/Brother/Printer/HL2270DW/cupswrapper/cupswrapperHL2270DW-2.0.4 || exit 1

echo -e "\nNext steps: "
echo "Make sure printer shows up in cups config @ http://127.0.0.1:631"
echo "Edit /etc/cups/printers.conf and change the DeviceURI from &#8216;usb:xxxxx&#8217; to &#8216;file:///dev/usb/lp0&#8242; (or usb/lp1 or whatever exists, no quotes)."
echo -e "Restart cups\n"

```

---

### Post by mister_c on 2012-05-15
Works for me, thanks!

---

### Post by kurt18947 on 2012-05-16
Yes the HL-2270DW seems to have been a problem child.  Brother has a bash script to install any printer and it appears to work on 32 or 64 bit systems.  I've used it on a couple machines trying to diagnose another Brother printer problem and it seems to work pretty well.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104).

It'd be nice if there were a GUI but Brother seems happy to require CLI usage.  The biggest trick for those unfamiliar with CLI is knowing how to launch the script, I think.  Once it's running it's pretty straight-forward.

---

### Post by willejos on 2012-05-20
> **kurt18947 said:**
> Yes the HL-2270DW seems to have been a problem child.  Brother has a bash script to install any printer and it appears to work on 32 or 64 bit systems.  I've used it on a couple machines trying to diagnose another Brother printer problem and it seems to work pretty well.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104).

It'd be nice if there were a GUI but Brother seems happy to require CLI usage.  The biggest trick for those unfamiliar with CLI is knowing how to launch the script, I think.  Once it's running it's pretty straight-forward.

Thanks, it worked for me. I was having page alignment issues with my script and wanted to see if installing with Brother's would fix them but there's no difference. Webpages and gedit headers get cut off and the page is always aligned a little too far to the left.. This is with US Letter 11" x 8.5" set up in cups. Better than nothing anyway.

---

### Post by jedispork on 2012-07-28
Thanks! Very happy to have a working printer in Ubuntu. However I am using the 32 bit version of Ubuntu for these drivers alone.  Looks like a lot of hassle to get them working under 12.04 64 bit. 

Maybe this is obvious but you can use "Save link as"  when downloading the script from brothers site to send it to your download directory.

---

### Post by hundred1906 on 2012-08-23
Could you indicate how to run the script. I assume you copy it from the code window above .. then what?

---

### Post by jedispork on 2012-08-23
I will try to help. When you click on the link to download the tool (from the brother instructions page) it will take you to the agreement page. You can right click on I agree and use "save link as".  Then navigate to where you downloaded the file and right click and use "run terminal here". The directions mostly make sense from here. Just make sure you replace brother machine name with your correct model.

Hope that helps.

---

### Post by hundred1906 on 2012-08-24
Here is what I found.

Firstly the Brother Script did not download, it just opened up in a browser sub window. Instead I copied the entire script in the post above from willejos.

I copied the script into a file - in my case ~/Downloads/PrinterInstall but any place will do.

Use Synaptic, apt-get install or Ubuntu Software Centre to install 'bsdtar' Do this first because the script will only complain if it cannot find it.

Run the script from a terminal window using ```
sudo bash ~/Downloads/PrinterInstall
``` inserting your chosen file name instead of mine.

The script asks for the location of your initscript directory and gives a couple of options. Using 12.04 I chose option 1.

In my case the script went on from that point to complete with the suggestion to Edit /etc/cups/printers.conf

However I am using the printer in wireless mode. To get it into that mode I first connected it to my network through the router and configured it with my WPA passphrase. This involved accessing the printer through it's web interface. There is also a button sequence needed to put it into wireless mode - its in the printer documentation.

Finally I started the Printing application and selected Properties for the new printer. It is necessary get the application to search for the network printer location on the Settings Tab - the URI entry Change button. It's a bit obscure now as to how this worked but but it involved letting the system find the printer and then selecting it from a list, however I ended up with this as the address entry" dnssd://Brother%20HL-2270DW%20series._pdl-datastream._tcp.local/ " (without the quotes). This seemed to work in my case on two separate computers networked onto the one printer. I also changed the Options settings to DuplexNoTumble for double sided printing. There is also a Toner Save option that I have initially turned on.

I did not edit /etc/cups/printers.conf as suggested.

Finally I restarted CUPS via the terminal using ```
sudo /etc/init.d/cups restart
```

It all seems to work - so far.

---

### Post by revnerd on 2012-11-17
For some reason, I cannot get to the "choose driver" page, or the duplex on off page or anything. I have a two test print jobs waiting, on processing since yesterday and the other pending. 

Any help?

---

