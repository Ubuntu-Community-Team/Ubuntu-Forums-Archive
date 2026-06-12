---
title: "XSane support for Memorex MEM48U"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by sadalmelik57 on 2006-10-12
These forums have been so much help getting me into Ubuntu, if this were the time and place I'd sing the praises of both!  But my immediate problem is a Memorex MEM48U scanner that XSane v0.97 says is an "unsupported device" while the Xsane website says it has "good" support.  This is one of two obtacles that will chill the deal if I try to get my wife to switch to Ubuntu full time.

Following the advice I've read in other posts, I've re-loaded Xsane, installed the latest version of HPLIB, re-installed LIBUSB as well as LIBUSB-dev.  I unplugged the USB cable and tried different USB slots.  I tried KOOKA but it found no devices.  I coded in terminal - **cat /proc/filesystems**.  According to the Ubuntu HowTo for scanners I should see **no dev usbfs** (it is there) and **no dev usbdevfs**, which is not there.  I considered downloading the latest libusb, v 0.1.12, since the package loaded by Ubuntu is identified as 0.1-4, but I'm a bit afraid of using a package that Ubuntu doesn't support.

Any ideas what to do?

Progress made: 
Taking a queue from [https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)
I edited the configuration file at /etc/sane.d/dll.conf file with gedit.  I  added 48u to the list of supported devices.  Now XSane opens.  But once it opens it doesn't seem to be talking to my scanner.  I request a preview, it just shows a black square.  I tried "copy" and got my printer to spit out a very nice black square, but the scanner doesn't blink.  The light is on (but nobody's home).  Still plugging away at it, but I'd really like some ideas if anybody can give me a clue!:-k

Scratch that - XSane opened because I removed the "#" from "test" in the dll.conf file.  It had nothing to do with adding "48u" or any other reference to the scanner to dll.conf.  I thought I'd made progress, but I'm back to start.](*,)

---

### Post by sadalmelik57 on 2006-10-20
No responses received.  After contacting another Ubuntu user with a Memorex 48U scanner, I've come to the conclusion that this hardware is not supported, in spite of what the XSane website says.  Score one for Windoze.

---

### Post by matchstich on 2006-12-21
[http://www.linuxquestions.org/questions/showthread.php?t=393875&highlight=memorex+scanners](http://www.linuxquestions.org/questions/showthread.php?t=393875&highlight=memorex+scanners)

this link show's how to intall them, i have one also,

---

### Post by gorg on 2007-02-13
Dear Customer,

Sorry, the scanner just work under Windows system.

Best regards

Customer Service
Adam Yuan
Ultima Electronics Corp.
Tel:  886-2-2225-8998, Ext: 7206
Fax:  886-2-2225-2674
E-Mail address: [email]Adam_yuan@ultima.com.t                    info                                      
                                                                
      
                                               &#25910;&#20214;&#20154;&#65306; 
[email]Adam_Yuan@ultima.com.tw[/email]                                         
              
                      2007/02/13 08:52         &#21103;&#26412;&#25220;&#36865;&#65306;       
                                                                
      
                      AM                       &#20027;&#26088;&#65306;   re: 
mem48u                                                          
          


Dear Adam,

This email is about scanner.

Steve



      &#25910;&#20214;&#20154;&#65306;    [email]info@ultima.com.tw[/email]
      &#21103;&#26412;&#25220;&#36865;&#65306;
      &#21103;&#26412;&#23494;&#36865;&#65306;
      &#20027;&#26088;&#65306;      re: mem48u


2007/02/03 08:19 PM EST
            <font size=-1></font

hi, i have a mem48u scanner. i really like it. worked pretty 
good.
i switched to ubuntu from windows.
but, i can't seem to make it work on this operating system.
could you get me in touch with your engineers?  i would be 
willing to be a
test machine for getting
a driver out that would make the mem48u work in ubuntu.
i am not the only person looking to have this happen.
a few other folks have the same model scanner and are wanting 
it to work.
any help from y'all would be greatly appreciated.
thanks

---

### Post by mrbungle on 2007-04-23
dear memorex you have no idea what you are talking about.

it's pretty obvious the guy was just about ready to go for lunch:) 

i have the same scanner i have been trying to get to work and finally after reading this
[https://help.ubuntu.com/community/ArtecEplus48uConf](https://help.ubuntu.com/community/ArtecEplus48uConf)

i had success!!!

just make sure you have the installation cd because you need a file off of that.  if anyone needs the memorex file you can send me a message and i will send it to you.

---

### Post by matchstich on 2007-04-24
thanks, i followed the advice on the link you gave.

cept  when i go to applications-graphics-xsane image scanner or gimp

they just hang.

same reason my epson perfection 1200 quit working.

they will open and say they are searching,
but, then nothing happens. have waited for a long time

for xsane i have to force quit

for gimp, i have to reboot

thanks

---

### Post by mrbungle on 2007-04-24
you might be having a different problem then.

the error i was getting with my memorex scanner was
> Failed to open device 'artec_eplus48u:libusb:001:003': Invalid argument


never had any hanging problems just that error.

---

### Post by matchstich on 2007-07-13
i upgraded to feisty. 

and followed the directions in that link.

i got xsane to open .

but, when i click on scan , all i hear from the scanner is clicking noise.

like a gear is stuck.

any ideas.

---

