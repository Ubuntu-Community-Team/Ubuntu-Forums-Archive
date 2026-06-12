---
title: "Network share drive - having Nautilus probs"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by rogerdean on 2007-08-15
Hello all

I've just wired a LaCie Ethernet Disk mini into my router, and am trying to set up access to my Linux terminals. I've set the IP as static, it's formatted by default in XFS which I think should be ok, and I can access it fine in Windows, and also in Linux using Firefox and gFTP but crucially not Nautilus.

In Firefox I can access the shared drive from [ftp://192.168.0.30//roger/](ftp://192.168.0.30//roger/) 
In gFTP I can read and write from host:192.168.0.30, folder:/roger/
(with the default username and password)

However, despite trying everything I can think of, Nautilus declines to access the drive. There's a password set up in the Keyring, and I've tried going in via Go->Location... and File->Connect to Server... but no joy. 

When I type [ftp://192.168.0.30](ftp://192.168.0.30) error message is -

The folder contents could not be displayed. Sorry, couldn't display all the contents of "ftp: 192.168.0.30". 

Not a hint why...

When I try [ftp://192.168.0.30/roger](ftp://192.168.0.30/roger) I get

Nautilus cannot display "ftp://192.168.0.30/roger". Please select another viewer and try again.

Is this a clue? Does Nautilus need a supporting package?

Can anyone help me out here?
Many thanks indeed
Roger



UPDATE -
Have managed to get in via Samba
smb://192.168.0.30/roger
but I shouldn't need this should I?

---

### Post by rogerdean on 2007-08-15
right, feel a bit silly. don't know what i changed but i seem to be able to connect via ftp within nautilus now...

---

### Post by telemap on 2008-04-16
Hello,

Could you tell me which version of Nautilus you are using because I can't connect to my Lacie Ethernet mini Disk ?

Thanks in advance.

Pat

---

