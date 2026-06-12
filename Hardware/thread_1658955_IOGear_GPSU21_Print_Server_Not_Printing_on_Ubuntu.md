---
title: "IOGear GPSU21 Print Server Not Printing on Ubuntu"
date: 2011-01-03
forum: Hardware
---

### Post by mxgods on 2011-01-03
I have an HP Photosmart D5460 printer on a IOGear GPSU21 print server.  When I plug the printer directly into my Ubuntu 10.10 desktop, it works fine.  If I connect to the printer shared from a Windows Vista computer, it prints fine.  But if I connect to the SAMBA share on the print server it does not work.  The error message is "Error writing spool: Call timed out: server did not respond after 1000 milliseconds."  If I use a windows computer to connect to the Samba Shared printer on the print server it works fine.

---

### Post by Poser55 on 2011-01-05
I got mine to work with a Dell 1110 through CUPS. 
I set the System, Administration, Printing, Server, Settings by clicking the first four boxes
Then I went to the cupsd.conf file in the /etc/cups directory and added three lines, all the same.

<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  **Allow all**
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
**  Allow all**
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
 ** Allow all**
</Location>

Also note that the first five lines of my file looked like this:
LogLevel warn
MaxLogSize 0
SystemGroup lpadmin
# Allow remote access
**Port 631**
Listen /var/run/cups/cups.sock

I think the check boxes in the server settings do this and that the Port 631 line is the operative one.

After this, the printer showed up.

If you aren't sure how to edit a protected file, here's how I did it.

Applications, Accessories, Terminal will open a terminal window
cd /etc/cups will put you in the right folder
sudo nano cupsd.conf will open the file in a simple editor without mouse support after asking for your root password
You can then edit the file using your arrows and delete keys
When you are done press ^x (control and x at the same time)
Say yes to save
Hit enter to keep the name

Good luck.

u

---

### Post by mxgods on 2011-01-06
> **Poser55 said:**
> I got mine to work with a Dell 1110 through CUPS. 
I set the System, Administration, Printing, Server, Settings by clicking the first four boxes
Then I went to the cupsd.conf file in the /etc/cups directory and added three lines, all the same.

<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  **Allow all**
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
**  Allow all**
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
 ** Allow all**
</Location>

Also note that the first five lines of my file looked like this:
LogLevel warn
MaxLogSize 0
SystemGroup lpadmin
# Allow remote access
**Port 631**
Listen /var/run/cups/cups.sock

I think the check boxes in the server settings do this and that the Port 631 line is the operative one.

After this, the printer showed up.

If you aren't sure how to edit a protected file, here's how I did it.

Applications, Accessories, Terminal will open a terminal window
cd /etc/cups will put you in the right folder
sudo nano cupsd.conf will open the file in a simple editor without mouse support after asking for your root password
You can then edit the file using your arrows and delete keys
When you are done press ^x (control and x at the same time)
Say yes to save
Hit enter to keep the name

Good luck.

u
Ok that wroked.  The only thing i had to do was add the printer a little differently.  It didn't just show up for me.  In addition to your steps:

In System -> Administration -> Printing click the Add button.
Select other and type in http://<ip-address-of-print-server>:631/lp1
Click forward
Select the printer brand then model.
Click ok
print a test page 
and it worked perfectly.

My guess is it must have something to do with the check box for allow internet printing and the print server not allowing ipp:// instead of [http://.](http://.)  Thanks for your help, i  was really starting to rack my brain.

---

