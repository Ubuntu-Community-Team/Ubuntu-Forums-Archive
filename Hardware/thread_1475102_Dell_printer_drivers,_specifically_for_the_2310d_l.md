---
title: "Dell printer drivers, specifically for the 2310d laser printer"
date: 2010-05-06
forum: Hardware
---

### Post by guaka on 2010-05-06
I'm trying to install a Dell 2230d laser printer.  I found some drivers for Linux here:

[http://support.euro.dell.com/support/downloads/download.aspx?c=nl&l=nl&s=gen&releaseid=R216933&formatcnt=0&libid=0&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=308524](http://support.euro.dell.com/support/downloads/download.aspx?c=nl&l=nl&s=gen&releaseid=R216933&formatcnt=0&libid=0&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=308524)

Well, actually I had to find out this from the HTML source: 
wget [http://ftp.us.dell.com/printer/Print_drivers-linux-glibc2-x86.rpm](http://ftp.us.dell.com/printer/Print_drivers-linux-glibc2-x86.rpm)

I created a deb package with alien, which I installed with dpkg.

sudo apt-get install alien
alien Print_drivers-linux-glibc2-x86.rpm
sudo dpkg -i print_drivers-linux-glibc2-x86.deb

Then I had to add a symlink:

cd /usr
sudo ln -s /usr/local/dell/unix_prt_drivers/ dellprint

..in order to finally launch the /usr/local/setup.dellprint script.

Then I restarted cups:

sudo /etc/init.d/cups restart

And... it's not working yet.  Anyone had more luck with these?

---

### Post by guaka on 2010-05-26
I found the solution:

[LIST]
[*]make sure foomatic-db is installed
[*]when you connect the printer you choose your driver, choose the driver for the S2500
[*]at printer options: change page size to A4 (possibly only need if your printer is A4)
[*]print test page
[/LIST]

---

### Post by SnappyCrunch on 2010-08-18
I wanted to say that these steps worked great for me, with the exception that the line that reads 
```
/usr/local/setup.dellprint
```
should actually read
```
/usr/local/dell/setup.dellprint
```

Thanks!

---

