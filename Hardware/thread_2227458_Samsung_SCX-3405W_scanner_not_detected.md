---
title: "Samsung SCX-3405W scanner not detected"
date: 2014-06-02
forum: Hardware
---

### Post by kuckunniwi on 2014-06-02
Hi all,

I'm having some issues with my Samsung multifucntion printer/scanner and wondered if there might be an altruistic soul out there willing to spend a couple of minutes helping me to figure it out. 

My printer is a Samsung SCX-3405W, which I connect to over the network. I've been using the [Samsung Unified Linux drivers]("http://www.bchemnet.com/suldr/index.html"), which worked flawlessly under Kubuntu 13.10 amd64 - both the printer and the scanner (which was effortlessly detected with Xsane, Simplescan, Skanlite...). After doing a fresh install of Kubuntu 14.04 amd64, I can no longer get the scanner to work (printing works fine)

I installed, just as the previous time, "suld-driver-4.00.36" and "suld-configurator-2-qt4".

None of my scanning apps detects the scanner (Skanlight, Xsane...). Suld-configurator doesn't detect it either. I removed "suld-driver-4.00.36" and installed 4.00.39.

No changes.


```
$ sudo scanimage -L
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```


- "suld-network-2" is the latest version.

- Have already gone through all the steps in the "Scanner Questions" troubleshooting in the [SULD scanning troubleshooting section]("http://www.bchemnet.com/suldr/scanning.html").

- Added my user to the "lp" group

- The scanner isn't being detected by my system:

```
/opt/Samsung/mfp/bin/netdiscovery --all --scanner


# DEBUG: Network printers discovery utility

```

```

/opt/Samsung/mfp/bin/netdiscovery -s --snmp

# DEBUG: Network printers discovery utility
```


- Both devices (laptop and scanner) are on the same network.

- Firewall is disabled

- Tested the scanner on a friend's laptop (Xubuntu 13.10 amd64) using 4.00.36 drivers, and it works fine. 


I've already asked around in the SULD forums,  and was told that:

> I suspect that something, perhaps the SANE version, that changed from 13.10 to 14.04 is the actual problem.  


Does anyone have any ideas what I could do to solve this? I'm self-employed and use the scanner on an almost daily basis, and would be infinitely greatful if someone could help me check this out / point me in the right direction. Any additional info I can provide to make diagnosis more reliable, let me know!

Thanks in advance!

---

### Post by kuckunniwi on 2014-06-02
PROBLEM SOLVED.

The problem, as had been suggested to me in the SULD forums, came from SANE. Looking through their documentation, I was able to find that the problem resided in /etc/sane.d/xerox_mfp.conf; the line for my printer was commented, and the printer was set in USB mode:

```
#Samsung SCX-3205W, usb mode
```

I uninstalled suld-driver-4.00.39 and installed 4.00.36, since, for some reason, 4.00.39 only lets me add the printer in DNS-SD mode (as opposed to tcp host address +port)

Rebooted, added the printer again via network address+port, then uncommented and edited the pertinent line in /etc/sane.d/xerox_mfp.conf so it looks like this:

```
#Samsung SCX-3205W, network mode
tcp host_address [port]
```

Problem solved. :)

I hope this comes in handy - for future reference - for anyone else experiencing the same kind of problem.

---

### Post by kuckunniwi on 2014-06-05
EDIT:

Just for the record, for some reason, in Kubuntu 14.10 amd64, certain apps (e.g. Okular) are unable/unwilling to print when this printer is used in tcp address+port mode. 

To get it to work, I had to add the printer again as an LPD network printer (DNS-SD) and make this printer default, while leaving the TCP-mode printer (how it was previously installed) untouched, so as to maintain scanner functionality.

---

### Post by jsacks on 2015-06-01
Hi, can you explain how you fixed this problem in more simple language and preferably writing out each step you took?

I'm having the same problem. Printing works via USB but scanning doesn't. It also does not detect it over the network. Thanks.

---

### Post by kuckunniwi on 2015-06-02
Hi,

Actually, once upon a time the scanner stopped working (updated SANE? I do not know) and I still haven't been able to get it fixed. Linux support for this printer is proving difficult to find. Network printing does work though. But, here's what I did to get at least that part working:


1) INSTALL REPOSITORIES

    Using the terminal:
        
        Enter the following in a terminal (as root):

```
sudo bash -c 'echo "deb http://www.bchemnet.com/suldr/ debian extra" >> /etc/apt/sources.list'
```


2) Install the GPG key (last update: 18 Oct 2009) for the repository (if you skip this step, you will get warnings about installing unauthenticated packages).

    In a terminal, as root, enter the command (the - marks are important):

```
sudo wget -O - http://www.bchemnet.com/suldr/suldr.gpg | sudo apt-key add -
```
        
    
Download the key file and execute the following (as root) in a terminal, in the folder with the key file:
    
	
    Refresh your repository listings:

    On a terminal (as root):

```
sudo apt-get update
```
    

3) INSTALL THE DRIVERS (these were no most recent versions back when I installed. Check [http://www.bchemnet.com/suldr/]("http://www.bchemnet.com/suldr/") for more up-to-date ones, then simply replace the version number below for the one you'd like to install. 

```
sudo apt-get install suld-driver-4.00.39

    sudo apt-get install suld-configurator-2-qt4
```

    Reboot system

    Add the printer from your distro's usual printer managing tool. It should detect it wirelessly (supposing you've configured it to connect to your network), then simply choose the right drivers. 


NOTES:

    To install the driver for printing and scanning (if your printer has a scanner), select one of the suld-driver-* packages to install. Chances are that the suld-driver-4.00.39 package will work for you. The latest releases are suld-driver-4.01.17, which drops support for some printers but includes support for the new Xpress line, and suld-driver2-1.00.06, which adds arm support and a few additional printers but is not compatible with most of the other packages. Check the list of supported printers if the driver does not seem to be working for you. 

    Regardless of the particular package installed, you will then need to set up the printer using any printer management tool (the default one in your distribution, the CUPS web interface, or the Samsung Configurator).
    
    If you want to use Samsung's graphical interface for managing the printer/scanner (instead of the default printer and scanner management tools in your distribution), you can install one of the suld-configurator-* packages. (If using the driver2 packages, the Configurator is not available, and you will have to use a distribution tool.) Most people will probably want suld-configurator-2-qt4. 

Good luck!      :)

---

