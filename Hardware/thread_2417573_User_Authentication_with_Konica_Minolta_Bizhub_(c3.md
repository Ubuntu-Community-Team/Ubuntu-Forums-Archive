---
title: "User Authentication with Konica Minolta Bizhub (c360 and similar)"
date: 2019-04-24
forum: Hardware
---

### Post by rpkzarathustra on 2019-04-24
In case someone has the same issue: 

We have a Konica Minolta Bizhub C360 which needs user authentication for printing. However, you can authenticate as public or guest user without password for printing black and white and with a specific username and password for printing color. 

I used this tutorial: [link]("https://ubuntuforums.org/showthread.php?t=2292528")

But here the caveat and/or tips: 

**In step 1** of the above mentioned tutorial the line to add in the PPD-File was missing in my case later on after installing the driver. However, I was able to see the installed PPD-file in step 4 (location: /etc/cups/ppd/). I added the said line there and had no problems with that. 

**In step 4** of the above mentioned tutorial the acccount name was in my case "Public" (line: ACCOUNT_NAME="Public"). I left the password empty and it worked.

---

