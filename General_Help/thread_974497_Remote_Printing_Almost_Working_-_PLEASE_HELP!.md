---
title: "Remote Printing Almost Working - PLEASE HELP!"
date: 2008-11-07
forum: General Help
---

### Post by joel@parke.ods.org on 2008-11-07
Hi,

Until today, remote SAMBA printers and files were not browsable from Vista.  Now today - hurrah - after updating, I can browse folders and printers and even connect to my SMABA printer on Ubuntu.  

BUT when I attempt to print - have the following errors in the samba log files.
FIRST: laptopjwp.log (my client Vista machine)
[2008/11/07 14:47:07,  1] rpc_client/cli_pipe.c:cli_rpc_pipe_open(2227)
  cli_rpc_pipe_open: cli_nt_create failed on pipe \spoolss to machine laptopjwp.  Error was NT_STATUS_ACCESS_DENIED
[2008/11/07 14:47:08,  0] printing/print_cups.c:cups_job_submit(658)
  Unable to print file to Hewlett-Packard HP LaserJet 2200 - client-error-not-found
SECOND: smbd.log
[2008/11/07 14:47:48,  0] printing/print_cups.c:cups_queue_get(805)
  Unable to get jobs for ipp://localhost/printers/Hewlett-Packard HP LaserJet 2200 - client-error-not-found

Now this is either a bug or perhaps I need to tweak something in smb.conf (this file worked under 8.04).  I have listed my smb.conf file below. Please let me know if I need to tweak something, or just wait for another update!!!!

Thanks so much, 
Joel

smb.conf file:
# Global parameters
[global]
        level2 oplocks = no
        oplocks = no
        debug level = 1
        printing = cups
        printcap = cups
        server string = Samba Server
        encrypt passwords = true
        client ntlmv2 auth = yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *New*password* %n\n *Retype*new*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*
        unix password sync = Yes
        log file = /var/log/samba/%m.log
        max log size = 0
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        dns proxy = Yes
        disable spoolss = no

        interfaces = 192.168.1.0/255.255.255.0 127.0.0.1
        bind interfaces only = yes  

        workgroup = WORKGROUP
        security = user
        username map = /etc/samba/smbusers
        idmap uid = 16777216-33554431
        idmap gid = 16777216-33554431
        template shell = /bin/false
        winbind use default domain = no
        wins support = yes

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        create mask = 0664
        directory mask = 0775
        browseable = Yes

[HPHP]
        read only = No
        path = /var/spool/samba
        guest ok = Yes
        printable = Yes
        printer name = "Hewlett-Packard HP LaserJet 2200"
        use client driver = yes

[joel]
        path = /home/joel
        available = yes
        browsable = yes
        public = yes
        writable = yes

---

### Post by joel@parke.ods.org on 2008-11-07
Anyone have any luck getting printing on Ubuntu to work with Vista?  If so, could you post your smb.conf file?

Thanks!

---

### Post by joel@parke.ods.org on 2008-11-08
Anyone use samba and print???? Could you please post a working smb.conf so I can check if my problem is configuration of a bug I should report????

Thanks

---

### Post by aaronp on 2008-11-10
Hi,
I am having a similar issue.
I'm using the driver on the client side (Vista Home Premium laptop) but when printing a test page it will actually print, however the status messages from the printer aren't making it back to Vista so Vista thinks it has still submitted the job waiting for the printer to pick it up (as far as I can tell).
I have the same messages in my log file as you, every time I print or try to get the printer status.

---

### Post by joel@parke.ods.org on 2008-11-10
Glad to hear from someone!
Could you post your smb.conf file so that I could at least compare to mine and see what the differences are.  It is hopeful that you at least are able to print!

Thanks!

---

### Post by aaronp on 2008-11-10
Here you go, smb file below.
Note, I am using a locally installed driver on the Vista PC and just printing it raw.

Also, you will see from below that in the printers section that I had to explicitly state the users who I wanted to be able to print, because I had trouble getting it to print with the guest account.
Therefore, when I set up the printer, it asked me for a username/password and I put in my Ubuntu account credentials.

```

[global]
	workgroup = aas022313
	netbios name = Ubuntu8.04Server
	username map = /etc/samba/smbusers
	security = user
        load printers = yes
	printcap name = cups
	printing = cups

[homes]
	read only = no
	browseable = no


[printers]
comment = All Printers
path = /var/spool/samba
browseable = no
public = yes
guest ok = yes
writable = no
printable = yes 
valid users = aaron smbguest
use client driver = yes

[media]
path = /media
comment = Media
valid users = aaron smbguest
write list = aaron
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

```

---

### Post by joel@parke.ods.org on 2008-11-10
Thanks for the file!

NOW, Ubuntu seems to no longer see my printer though the USB->parallel adapter I was using... So I will have to wait a week or so for that new bug to be fixed....

Then I will try your smb.conf file.

---

### Post by aaronp on 2008-11-10
you have upgraded to intrepid?
fyi - I'm using hardy

---

### Post by joel@parke.ods.org on 2008-11-10
YES! I am using 8.10.  And I can not thankfully say that all my stopping points have been resolved.  

In terms of my printing problems.  I discovered that by using Windoze I was able to reset the USB -> parallel cable and that is not working.  

In terms of umb.conf I am embarrassed to admit that I had the name of the local printer device incorrect and that is why I had all the problems.  Now things are working properly.  

In terms of what I had under 8.04, it's about the same and that worked as well.  So I don't know what might be causing issues with your setup.

I do still see:
[2008/11/10 17:50:54,  1] rpc_client/cli_pipe.c:cli_rpc_pipe_open(2227)
  cli_rpc_pipe_open: cli_nt_create failed on pipe \spoolss to machine laptopjwp.  Error was NT_STATUS_ACCESS_DENIED

BUT everything prints correctly.

---

### Post by aaronp on 2008-11-10
Good to hear you got it working. Seems you and I are in the same boat re: the log file messages. 
It is not a huge deal for me as long as the printing works but I am a perfectionist so still want to get the status messages back to Vista to work properly.
If I manage to find a solution I'll post it here for you...

---

