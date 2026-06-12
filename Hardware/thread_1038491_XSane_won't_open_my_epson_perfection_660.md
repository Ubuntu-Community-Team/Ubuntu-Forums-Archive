---
title: "XSane won't open my epson perfection 660"
date: 2009-01-12
forum: Hardware
---

### Post by ejv on 2009-01-12
hi

i've been reading through similar posts but couldn't repair my problem, so here is this thread

XSane recognizes my scanner but when trying to open it it says:

snapscan:libusb:002:004': invalid argument (or something like that - it's a free translation from spanish)

i suppose i have to edit the snapscan file, but i don't know what i have to write instead of the "your-firmwarefile.bin" part.

thanks for the help...

ejv

---

### Post by jarondl on 2009-02-25
What you need to do is to download the windows drivers from epson :
[http://www.epson.com.sg/epson/drivers/driver_download.htm?dc=1&mode=3&m=false&catid=5&pid=46]("http://www.epson.com.sg/epson/drivers/driver_download.htm?dc=1&mode=3&m=false&catid=5&pid=46")
Then, extract DATA/BIN/TAIL_061.bin from the zip archive.
Copy that file to /usr/share/sane/snapscan (If it's on the Desktop, you can use:)
```
 sudo mkdir /usr/share/sane/snapscan
sudp cp ~/Desktop/TAIL_061.bin /usr/share/sane/snapscan/ 
```
Next you need to change this file's permissions, so the scanning software could read it:
```
 sudo chmod a+r /usr/share/sane/snapscan/TAIL_061.BIN 
```
Now edit the line in /etc/sane.d/snapscan.conf that says:
```
#firmware /usr/share/sane/snapscan/your-firmwarefile.bin
```
to
```
firmware /usr/share/sane/snapscan/TAIL_061.BIN
```
That was enough to make it work for me.
Good Luck

(Edited according to ejv's post here below)

---

### Post by xwindozer on 2009-03-18
Hi I am a noob and have the same problem with my epson 660 perfection scanner. It did work originally without any issues and then suddenly stopped. I don't know whether it had to do with downloading updates.

I have tried to follow your advice but don't find any snapscan folder in the sane folder to copy tail_061.bin to (only xsane and gt68xx)

Please help

---

### Post by ejv on 2009-03-28
i solved the problem with the help of GH88. 
Here i quote all the posts that we exchanged until the solution.
hope this will be useful...:)
bye 

ejv

Quote:
Originally Posted by ejv

hi
just read your message about the epson 660

i'm having the same problem

what do you mean when you say you passed the line from epson.conf to epson2.conf?

should i just erase the # at the beginning of the line and save? if that's it, it says i don't have the permissions to save...

thanks in advance
ejv


Quote:
Originally Posted by GH68
Hi ejv

I sent you a reply yesterday, but for some reason it is not in my "sent items mailbox", so maybe you have not received it. I have, however, updated the thread. Just one comment about your issue with the lacking permissions to save: You have to edit the file as root, i.e. use "sudo gedit /etc/sane.d/epson.conf" (or replace "gedit" with the editor you prefer).

Good luck,
GH

Quote:
Originally Posted by ejv
Hey, thanks for your message

I have to say I'm a bit stuck, and not quite sure of what to do. So:

How do you add the driver dowloaded from the epson page to /usr/share/sane? I download it, have a .zip folder im my desktop, find the file in /data/bin and when I unzip it, well just nothing happens. So i unzip it to my desktop and then try to copy it to /usr/share/sane but i don't have permission.

So i suppose i have to be root user (as you said). How? I type on the terminal sudo -i and am root but it still doesn't work.

finally and making it short: if you've got the time, could you explain me patiently what i have to do?

Thanks

ejv

Quote:
Originally Posted by GH68
It seems that you have managed to extract tail_061.bin to your desktop, so I will assume that (please note that Linux is case sensitive, the name might be Tail_061.bin and then you either have to rename it or use a capital "T" in the beginning where I use lowercase "t"). Open a terminal window and type the following to make sure that you are in your home directory:
Code:

cd

Then type the following to try to figure out what the name of your desktop directory is:
Code:

ls

It is probably "Desktop" (in my case it is "Skrivbord", since I have a Swedish installation). I will now assume that it is "Desktop", but if not, replace "Desktop" in the following command with the name of the directory that is your desktop. Type
Code:

sudo cp Desktop/tail_61.bin /usr/share/sane/.

If other people than the root (su) should be able to scan, you have to make this driver file readable to all. To do that, type the following:
Code:

chmod a+r /usr/share/sane/tail_61.bin

Good luck! Don't hesitate to ask me again, and please let me know if you succeed!


Originally Posted by ejv
Hey THANKS! It finally worked! Really thanks a lot man!


ejv







GH68 is offline   	Forward Message

---

