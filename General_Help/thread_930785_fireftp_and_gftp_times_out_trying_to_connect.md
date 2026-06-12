---
title: "fireftp and gftp times out trying to connect"
date: 2008-09-26
forum: General Help
---

### Post by melojo on 2008-09-26
I hope someone can give me an idea what the problem is. My web hosting company doesn't

I am trying to access my website through ftp and it just times out.
I can login and connect through an ftp terminal but not through a gui ftp program.
It seems to log me in but can't get the files to show from the server it just times out.  Below is from the gftp log.

Trying ftp.*****:21
Connected to *****:21
220 ****** Limited Use FTP Server Awaiting Login
USER ********

331 User name ok, need password.
PASS xxxx
230-Thank you for using **********!  Please read the following message
230-for important information and guidelines that should answer basic
230-questions about the ******** FTP service.
230-
230-*  You do not have a file size limit restriction for uploading your
230-   files.  You will, however, be restricted by the amount of storage
230-   that is available in your account.
230-
230-*  You cannot upload more than 20,000 files total per Web site.
230-
230-We hope you enjoy using the ******** FTP service.
230-
230-If you have any technical questions for our Support Team, please log
230-into your ******** account and create a new Help Ticket in the Help
230-Center.
230 End of message.
SYST

215 UNIX Type: L8.
TYPE I

200 Type set to I.
PWD

257 "/" is current directory.
Loading directory listing / from server (LC_TIME=en_US.UTF-8)
PASV

227 Entering Passive Mode (209,157,71,109,156,70)

---

### Post by fragos on 2008-09-26
FireFTP, gFTP and MaemoFTP on my N810 work fine with GoDaddy. You didn't mention who your Hosting company is or if the site is hosted on Linux or Windows server.

---

### Post by melojo on 2008-09-26
My hosting company is vistaprint which has something to do with homestead.com.  I have been thinking of switching to godaddy.  I have yet to get a reply from my last correspondance with homestead.

---

### Post by fragos on 2008-09-26
GoDaddy serves me well at a reasonable price. I highly recommend a Linux hosting package.

---

### Post by melojo on 2008-09-27
> **fragos said:**
> GoDaddy serves me well at a reasonable price. I highly recommend a Linux hosting package.

In the process of changing to godaddy now

---

