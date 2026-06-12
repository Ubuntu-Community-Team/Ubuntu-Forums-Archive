---
title: "A linux-compatible document scanner: Brother ADS-1000W"
date: 2013-12-14
forum: Hardware
---

### Post by linguini on 2013-12-14
I was looking for a document scanner to digitize my piles of paper, and was very disappointed to see how many of the current models don't seem to be linux-compatible. I was very close to giving up and buying a Canon P-215, which I would be forced to use on a mac or windows machine; but then I discovered the new Brother models ([ADS-1000W]("http://www.amazon.com/gp/product/B00EKW6JGI/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B00EKW6JGI&linkCode=as2&tag=tuktukcat-20") and [ADS-1500W]("http://www.amazon.com/gp/product/B00EKW6JZ4/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B00EKW6JZ4&linkCode=as2&tag=tuktukcat-20")), which have official support for linux! I couldn't find any discussions of these on linux forums, but since the ads-1000w was on sale at amazon I decided to give it a chance. And I'm happy I did!

I'll start with my favorite scanning method: you can configure the scanner to scan to an FTP server, with a pre-determined profile that you enter through a browser-based interface. There are 2 hardware buttons that you can map to different ftp profiles, so what I did was to setup an ftp server ([vsftpd]("https://help.ubuntu.com/community/vsftpd")) on my computer, and map one button to do color scans and the other button for black&white, and both upload the scan as a PDF file to my computer. Now I can scan without touching my computer, and it doesn't depend on any driver or scanning software. Works perfectly, and is very fast.

I also installed Brother's linux drivers and configured the scanner as a network scanner (it connects through wifi), and it works with gscan2pdf, except for 2 problems: 1) I couldn't get duplex scan to work (unlike in the ftp method); 2) the scanner options don't show up in gscan2pdf's scan dialog, so it just seems to use default settings.

You also have 2 more options: scan to a usb drive; or to an android tablet or phone. And of course, you can also scan to a mac or a windows pc; since this is a network scanner, you don't have to choose only one, all your computers/devices can share this scanner. (I did have to use windows to set up the wifi connection, by first connecting the scanner via usb, but after that there's no need for windows any more).

Overall, I'm very happy with this purchase; if you're looking for a small and moderately priced scanner that works well with linux, I think this is a very good choice.

(Full disclosure: the links above are my amazon affiliate links)

---

### Post by roger_1960 on 2014-01-23
Hi

Yes Brother support for linux is good.  I have used brother printer/scanners for many years (7)  DCP115C and more recently wifi DCP315J which all worked fine once the comprehensive installation instructions on brothers site are followed [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Roger

---

### Post by gifford on 2014-01-24
I agree with roger_1960 about the Brother linux support. Have used various Brother multifunction printers with great success without any problems. As pointed out, the key is to follow the instructions on the Brother site for installation.

---

