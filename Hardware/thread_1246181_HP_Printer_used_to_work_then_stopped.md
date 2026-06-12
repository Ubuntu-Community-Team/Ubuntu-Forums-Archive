---
title: "HP Printer used to work then stopped"
date: 2009-08-21
forum: Hardware
---

### Post by finch127 on 2009-08-21
Hey everyone, i got a good puzzle for you all:

So when 9.04 came out, i upgraded, and i remember in 8.10 what a hassle it was to get my printer working. I dont remember what i did then, i didnt think to write it down but I had to do it again for 9.04. Needless to say i didnt know how and gave up until a month or two later, my printer just gets auto-configured or something and on my next boot it magically starts working. It is tied to a Windows Computer on my brothers network, it doesnt have its own IP [its one of those crappy OfficeJet 6310xi printers]. Then a few weeks back it stops working, so i try to add the printer to the printer config again. It doesnt even detect it when i browse the network. It just doesnt appear in the SMB browser. 

I have really tried everything here, reconfiguring CUPS with the old device URI and the like : nothing. No matter what i do it just doesnt appear or work. 

Does anyone have a similar problem? Can anyone offer some insight?

Thanks ahead,
Finch

---

### Post by finch127 on 2009-08-21
Alright I solved it, heres what i did (I already have HPLIP installed):

1. First i went to /etc/samba/smb.conf and i changed the workgroup to the windows workgroup name just in case. I also uncommented these lines (load printers and printing/printcap):

```

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = yes

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

```

2. I restarted CUPS after this (NOTE: earlier I said I downgraded CUPS: DO NOT DO THIS!!! I have a good feeling it bricked my printing system and now i must reinstall everything... I recently found it works without downgrading)
```

sudo service cups restart

```

to restart CUPS and then...

3. I went to 
```

http://localhost:631

```
to access the CUPS web interface and i proceeded to add my printer. This time around i used the smb:// protocol but i had a trick up my sleeve. I found the print host IP by running nmap on my network. This will be different for all of you depending on your router's make and model but mines a buffalo so the local IPs are 192.167.1.xxx

```

nmap -sP 192.167.1.1-255

```

and found PRINTHOST @ 192.167.1.101

4. Back at the CUPS interface, I then inputted smb://HOME/192.167.1.101/HPALLINONE [my device URI from earlier in the year but i changed the server name to the IP address] and configured the ppd file etc and it worked.

Hope this can help some of you!

---

### Post by finch127 on 2009-08-22
Ok I had another issue and fixed it. Maybe this is a result of the last fix, but if any of you followed it, here it is:

1. I couldnt use the printer and when i went to the printer management bar the new option was gray and there was no printer. I tried hitting connect but it said it could not connect. I tried viewing the CUPS config in my web browser at localhost:631 but it was no luck.

2. It was then that i used:
```

sudo service cups restart

```
  cupsd came back and threw an error that the "child process exited with status 1."

3. I checked out /var/log/cups
```

cat error_log

```

and i got this:

```

E [22/Aug/2009:11:46:50 -0400] Unknown Policy Limit directive AuthType on line 21.
E [22/Aug/2009:11:48:59 -0400] Unknown Policy Limit directive AuthType on line 21.
E [22/Aug/2009:11:49:02 -0400] Unknown Policy Limit directive AuthType on line 21.
E [22/Aug/2009:11:51:35 -0400] Unknown Policy Limit directive AuthType on line 21.

```

4. So for any of you who have this problem, what i did was I editted the cupsd.conf (/etc/cups) file and on line 21 and any subsequent line that had this or anything similar:

```

<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
</Location>

```

I changed it to:

```

<Location /admin/conf>
  AuthType None
  Require valid-user
  # Restrict access to the configuration files...
  Order allow,deny
</Location>

```

Basically I changed its authorization type and Requirement setting so anyone can use the resource. I suppose this was a permissions error but instead of trudging through forums for that, I just changed it in the config file.

Enjoy!

---

### Post by finch127 on 2009-08-22
Alright the last issue with the "permissions" was not a fix it was a patch. I am getting many more different errors now which I am attempting to resolve. It may be more worth it to reinstall CUPS completely, I have a feeling that my earlier downgrade bricked the system.

I repeat, DO NOT do the downgrade procedure, it is too high risk and for most cases CUPS is sufficient. It was my mistake.

---

