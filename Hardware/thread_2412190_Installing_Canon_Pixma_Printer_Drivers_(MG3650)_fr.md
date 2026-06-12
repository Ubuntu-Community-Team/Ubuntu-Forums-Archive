---
title: "Installing Canon Pixma Printer Drivers (MG3650) from Canon's Website"
date: 2019-02-09
forum: Hardware
---

### Post by JayArtist on 2019-02-09
Hi,

I've been away from Linux for a few years now, I remember some things well, but I'm aware that some others things may have changed.

I have a Canon Pixma Mg3650 Printer/Scanner with Wi-Fi (or cable - but I prefer the Wi-Fi option). 
I also have download the .deb driver packages for the Printer model and Scanner from Canon's website.
I'm running Deepin Linux for now, but I know the same applies to Ubuntu.

The .deb files have a 'install.sh' file type and I am able to run/install (they are executable).

The problem though is there is a missing package according to the installer, but I have no idea what that package is. In the distant past, I had issues with a missing library file with a similar Canon Pixma printer, but this may well be different these days. 

```

An error occurred. A necessary package could not be found in the proper location.
```


I wish to use the manufacturer drivers as there are some specific features that they have that I require, especially the scanner.

Does anyone know what the missing package is, and if so how to install it.

Cheers,

Jay.

---

### Post by brian_p on 2019-02-14
> **JayArtist said:**
> Hi,

I've been away from Linux for a few years now, I remember some things well, but I'm aware that some others things may have changed.
.

The Canon drivers are not needed for printing.

1. Get yourself a terminal and check that the AIO is visible to the system  with the command

   ```
driverless
```
                                                                                                                      
   The output should begin with ipp://.                                                                                
                                                                                                                       
2. In the same terminal execute

    ```
lpstat -a
```

   If your AIO is visible in the output, you should now be able to print from any application.                                                
                                                                                                                       
3. If your AIO is not visible in the output, open /etc/cups/cups-browsed in an editor and uncomment        
                                                                                                                       
    CreateIPPPrinterQueues All                                                                                          
                                                                                                                       
    and restart cups-browsed                                                                                            
                                                                                                                       
    ```
systemctl restart cups-browsed
```                                                                                      
                                                                                                                       
    You should now be able to print from any application.

---

### Post by JayArtist on 2019-02-14
Brian_p, it was nice of you to reply, however, as I stated in my post, I wanted to use the official Canon Drivers for both the Printer and Scanner (ScanGear). These drivers have features that I require - using the default ones with Linux aren't enough.

There is a missing library/package and I need to know what is missing. 

Thanks.

---

### Post by brian_p on 2019-02-14
> **JayArtist said:**
> Brian_p, it was nice of you to reply, however, as I stated in my post, I wanted to use the official Canon Drivers for both the Printer and Scanner (ScanGear). These drivers have features that I require - using the default ones with Linux aren't enough.

The printer and scanner functions are separate. I guess you intend to use scangear. What features are offered by the Canon printer package that are not offered by the Ubuntu method I suggested.

> 
There is a missing library/package and I need to know what is missing. 


What package did you download?

---

### Post by JayArtist on 2019-02-14
Hi Brain,

Canon's drivers are quite comprehensive and have numerous options for this and similar models of printer/scanner, too many to options to bother listing. I've installed the default driver previously for printing on a similar model to this one and I had many issues. So from past experience I know the Canon drivers are great and work well. There isn't many manufacturers that bother to make Linux drivers. The ScanGear Driver is really good and offers great control of the scanner, it one of the reasons I've stuck with Canon over the years.


[https://imgur.com/a/D4QX798](https://imgur.com/a/D4QX798)

[https://imgur.com/a/Zo4Wm6E](https://imgur.com/a/Zo4Wm6E)


The packages I download were:

IJ Printer Driver Ver. 5.20 for Linux (debian Packagearchive)
ScanGear MP Ver. 3.20 for Linux (debian Packagearchive)

I haven't attempted the ScanGear package yet as I obviously need the printer working first. It's also used as a wi-fi printer. I'm currently waiting on a long lead so I can attach it manually to help with installation, as the wi-fi can be problematic to install.


From this link:

[https://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mg_series/pixma_mg3650.aspx?type=drivers&language=EN&os=Linux%20(64-bit)](https://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mg_series/pixma_mg3650.aspx?type=drivers&language=EN&os=Linux%20(64-bit))

---

### Post by brian_p on 2019-02-14
Hi JayArtist,

```
tar zvxf scangearmp2-source-3.50-1.tar.gz
```

unpacks the tarball to the directory cnijfilter2-5.20-1-deb.

```
dpkg -i cnijfilter2-5.20-1-deb/packages/cnijfilter2_5.20-1_amd64.deb
```

installs the Canon files on your system. You can now use your favourite software method to install a queue for the printer. This avoids having to sort out the issue with the install script (which basically does what I have advised, anyway). 

> 
I haven't attempted the ScanGear package yet as I obviously need the printer working first. It's also used as a wi-fi printer. I'm currently waiting on a long lead so I can attach it manually to help with installation, as the wi-fi can be problematic to install.


The scanner installation is independent of the printer installation.

---

### Post by brian_p on 2019-02-15
I do not have a Canon device and neither have I used scangear. Does its install script offer to set up network scanning or is it USB only?

---

