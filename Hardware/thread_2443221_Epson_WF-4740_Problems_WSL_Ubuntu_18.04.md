---
title: "Epson WF-4740 Problems WSL Ubuntu 18.04"
date: 2020-05-12
forum: Hardware
---

### Post by muencht on 2020-05-12
This posting details the problems I had trying to get an Epson Workforce WF-4740 networked printer (installed on Windows) to work on WSL Ubuntu 18.04 LTS. Originally this was a question but I was able to get it working before I posted. 

It is important to note that WSL (Windows Subsystem for Linux) is not "real" Linux; it is more of a Linux emulator. Many things that work with "real" Ubuntu 18.04 do not work with WSL. I spent many hours trying to get this printer to work using Samba, USB and finally IPP. 

I. Samba

There are many, many 'Howto' resources for file and printer sharing between Windows and Linux using Samba. None worked for me because, after installing Samba, I could never get smbd (daemon) to run! I had numerous file permissions issues which I could not resolve. 

II. USB (Local) Connection

I thought this would work for sure with a direct USB connection between the Windows 10 host and my printer. I installed the Epson Linux drivers using qdebi which also installed the LSB dependencies such as lsb-printing. I then added my printer using

```
sudo /usr/sbin/lpadmin -p wf4740 -v usb:/EPSON/WF-4740 -P /opt/epson-inkjet-printer-escpr2/ppds/Epson/Epson-WF-4740_Series-epson-inkjet-printer-escpr2.ppd.gz -E

```

Everything seemed to be working at first; I could print a text file w/o error using lpr and the job showed in lpq; however the CUPS admin page [ localhost:631 ] showed "Waiting for printer to become available". I soon discovered there was no device /dev/usb so of course this could never work. This is another case of WSL not being "real" Linux; the first WSL Ubuntu 14.04 did not even support external USB drives! 

III. IPP

I finally found an article that said don't use Samba, use IPP! 

[https://askubuntu.com/questions/156863/configuring-samba-to-allow-use-of-cups-printer](https://askubuntu.com/questions/156863/configuring-samba-to-allow-use-of-cups-printer)

"The preferred way to connect a Windows client to a Linux print server is using IPP. It's a standard printer protocol based on HTTP, allowing you to profit from port forwarding, tunneling etc.  Configuration is very easy and this method is less error-prone than using Samba. IPP is natively supported by Windows since Windows 2000. To configure the server side you need to enable browsing in /etc/cups/cupsd.conf, by adding the line "BrowesAllow all". 

The article gives the following sample URI (replace 'printer_name' with the name of your printer):

http://host_ip_address:631/printers/printer_name

####

I was not happy(!) to find that substituting 'EPSOND8886' for printer_name did not work. I finally found the correct URI in the Epson (not CUPS) admin page under Services > Protocols

http://192.168.1.6:631/ipp/print

HOORAY! finally I could print. 

####

**NOTE 1**: A queued job often stalls and will not print. The cups error_log only shows "The printer is not responding" which is no help. The best solution I have found:

```
sudo -S service cups --full-restart

```

**NOTE 2**: IP addresses can of course change when using DHCP. I therefore replaced the address in

http://192.168.1.6:631/ipp/print

with my hostname.

---

