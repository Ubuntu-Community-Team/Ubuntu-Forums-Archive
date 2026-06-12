---
title: "HOWTO: Canon Pixma MG5300 Wireless Printing"
date: 2013-04-03
forum: Hardware
---

### Post by kraylus on 2013-04-03
After much Googling I finally found a way to get my Pixma printer to receive print jobs from my vanilla Lubuntu netbook. This will require the download of the Linux drivers for this printer which, for some reason, are only available from the Canon Asia website....

Before you read on, this is not instructions on how to connect to a printer on another Windows/Linux machine on your network. The automated printer setup should be able to handle that particular situation all by itself. This guide instructs you how to connect to a Canon Pixma printer that is connected directly to your router, wirelessly or otherwise.

[Click here to download the .deb package you'll need.]("http://support-sg.canon-asia.com/contents/SG/EN/0100395402.html")

If for some reason that link becomes dead, do a Google search for:

```
cnijfilter-mg5300series-3.60-1-deb
```

Once you've downloaded the package, extract it anywhere you please and go into the "packages" folder. From the command line, navigate to the packages folder and execute the following to commands in this order:

```
sudo dpkg -i cnijfilter-common_3.60-1_amd64.deb
sudo dpkg -i cnijfilter-mg5300series_3.60-1_amd64.deb
```

Alternatively, from the GUI, you can simply double-click each package and click "Install Package", if that's easier for you. Just be sure to install them in the correct order. Once you've got that done, you'll need to get the MAC address of your Pixma MG5300 from the printer itself. Use the wheel button to navigate to the "Device Settings" option. In there, you can go to "Lan Settings" and then "Confirm Lan Settings". You now have two options. The first lets you view the MAC address right from the screen on the printer (you'll have to scroll a ways, it's towards the bottom), and the second lets you print a Configuration Page that has all the information you'll need. Once you've obtained the MAC address, open up a terminal and execute the following (the X's are replaced with your MAC address):

```
sudo service cups restart
/usr/sbin/lpadmin -p MG5300LAN -m canonmg5300.ppd -v cnijnet:/XX:XX:XX:XX:XX:XX -E
/usr/sbin/lpadmin -d MG5300LAN
```

When I did this, I got warning messages about gnome keyring or some such. It didn't affect anything.

If you're using Ubuntu, go to System>Administration>Printing. If you're using Lubuntu, click Start>System Tools>Printers. Yeah, I know... it's not really a "Start" button, but I don't know what they call it. If you don't know where your printer configuration tool is at on your Ubuntu-based operating system, typing **sudo system-config-printer** in a terminal window should get you where we need to be.

In this window, you should see the MG5300LAN we just created in the terminal. Right-click the icon and select "Properties". On the following page, you'll see "Device URI" and then a text box that has your MAC address already in it. To the right of THAT, is a button that says "Change..."

Click it!

The next window that pops up isn't going to be fully populated right away. Give it a few seconds, and in the list to the left, you'll see a new section called "Network Printer" and underneath it will be the name of your Canon printer followed by the MAC address. Select that printer and click "Apply". Now, click "Print Test Page" and if everything went smoothly, the screen on your printer will indicate that it's receiving data and should start to print an Ubuntu Test Page.

Hope this helps anyone who might be running into the same issues I did!

Haven't tried getting the scanner function of my Pixma to work via the network, but I know both the printer and the scanner work great when plugged in directly through a USB cable. That's a project for another day.

---

