---
title: "Print to CD using Canon IP4200"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by penguintutor on 2007-11-21
Does anyone know how to print to CD using an IP4200.

The new printer drivers included in 7.10 include all the options to print to CD, but when I try I just get a flashing no paper indicator.

When I print with another operating system then the following process is followed:

Click Print
- Message pops up - "Do not insert CD until I say"
- Message changes to enter CD
- Place CD and caddy into the printer
- Click OK on the message

On Linux I don't get any of these messages and I suspect the printer is waiting for a certain code to indicate that the user has clicked yes. 


Also do you know the paper size that I should use in OOo (Drawing) to match up with the tray for a 5 inch CD? I can probably work the dimensions out using trial and error, but I don't want to waste CDs

Thanks
Stewart

---

### Post by penguintutor on 2008-02-08
I found the answer to my problem. Here it is for anyone else that is having the same problems.

Through some trial and error I found that the print was being sent to the normal paper tray rather than the CD printer. Because the CD tray is open, it doesn't print, but instead waits on user input. I then realised that the reason for this was due to the selection of the Media Type in the printer driver.

The printer driver needs the following options to be set:
Media Size: CD 5-inch
Media Type: CD (this may be in the advanced options)
Media Source: CD Tray


I have also created a template that can be used with OpenOffice.org Draw, to print onto the CD.
The only thing with this is that it does not print to the very edge of the CD. It does what I need, but if you want to be able to print over the entire CD then you may have to adjust the settings using the CD-Custom option in the printer driver. If anyone does find these settings, please post details, but I didn't want to keep wasting CDs for testing it.

[Download: OOo Drawing template for printing to CD on a Canon iP4200 printer]("http://www.penguintutor.com/blog/viewblog.php?blog=507")

---

