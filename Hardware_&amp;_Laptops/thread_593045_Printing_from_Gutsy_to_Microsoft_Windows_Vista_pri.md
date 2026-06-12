---
title: "Printing from Gutsy to Microsoft Windows Vista printer"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by richbl on 2007-10-26
Hello all,

After upgrading to Gutsy (7.10), I noticed that the interface for creating a new printer had changed. As it turned out, I had a tough time trying to figure out just how to get things working. I did manage to figure things out.

So, to install a printer that currently shared on a Vista computer, the trick for me was to use the following smb syntax:

<vista_machine_ip_address>/<printer_name>

Where **vista_machine_ip_address** is the machine where you have your printer installed, and **printer_name** is the share name of the printer.

For example, to install a new printer under Gutsy:

0) From System/Administration, open the Printing dialog
1) Click the "New Printer" button
2) In the Select Connection list box, choose Windows Printer via SAMBA
3) In the textbox on the right, preceded by "smb://" enter the smb syntax as indicated above, such as: 

smb://192.168.100.100/Canon

4) If your Vista shares are password-protected (which they should be for security reasons), check the Authentication required checkbox, and fill in the appropriate user information.
5) Click the "Verify..." button

The "trick" here was that, because I hadn't entered the appropriate information in my networking Hosts section (under System/Administration/Network, Hosts tab), my Ubuntu machine didn't know my Vista machine name, so I had to use Vista's IP address instead.

The bottom line: be sure to update your Hosts table, OR use an IP address when creating a new networked printer in Gutsy.

---

### Post by s.victor on 2007-10-27
Thank you so much!

I've been trying to do this since I upgraded to Gutsy. Actually in my case the printer was on XP machine, so i suppose it works on every Windows OS.

---

### Post by BuntuFreak on 2008-01-27
I have the reverse problem. My printer is connected to Gutsy and works fine. Problem is I want my Vista computer to be able to print to it. I haven't had any trouble getting it to work the other way. I would have thought Vista to Gutsy would be easier. I was wrong.

Any help appreciated.

---

### Post by richbl on 2008-01-27
> **BuntuFreak said:**
> I have the reverse problem. My printer is connected to Gutsy and works fine. Problem is I want my Vista computer to be able to print to it. I haven't had any trouble getting it to work the other way. I would have thought Vista to Gutsy would be easier. I was wrong.

Any help appreciated.

The issue of having your Windows machine seeing a printer managed by Ubuntu can be a little trickier because you need to manage your shares (both printer and folder shares) through Samba.

If you're not familiar with Samba, spend some time getting an overview of what it's all about, then jump right in:

--I'd recommend installing SWAT if you're not yet familiar with it. SWAT stands for Samba Web Administration Tool, and makes managing Ubuntu shares pretty easy.

--That said, I believe there are also ways to share printers/folders that are native to Ubuntu interface. If you don't care for SWAT, take a look at printer sharing from System -> Administration -> Printing. Similarly, if you want to share folders from within Ubuntu, check out System -> Administration -> Shared Folders.

Since I'm more accustomed to sharing devices through Debian, I tend to rely on Samba/SWAT more than the Ubuntu interface. Old habits die hard.

Best of luck.

---

