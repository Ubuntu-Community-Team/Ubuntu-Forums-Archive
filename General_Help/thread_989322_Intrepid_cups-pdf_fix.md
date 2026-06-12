---
title: "Intrepid cups-pdf fix"
date: 2008-11-21
forum: General Help
---

### Post by supradave on 2008-11-21
Does anyone know how to get around the cups-pdf problem of it not being able to access $HOME/PDF.  I understand I could change my permissions of my home dir to 777, but that's not a good solution.  I can do an 'aa-complain cupsd' and it will work, so it leads me to believe that it's a apparmor problem.  

Has anyone found a solution to fix the problem without having to run this command ad infinitum (well, at reboots).

---

### Post by jongkind on 2008-11-22
Maybe I don't understand your problem, but why would you need cups-pdf? In Intrepid you can select 'print to file' (either postscript or pdf), which works well.

---

### Post by dinarcon on 2008-11-23
hi supradave,

well... I had been having the same problem till a few moments ago, and this is how I solved it...

1.- Go to "System -> Administration -> Synaptic Package Manager"
2.- Search and install "cups-pdf"
   2.1.- I read that "cups-driver-gutenprint" has to be installed as well. In my case, it was already installed.
3.- [by [stinger30au]('http://ubuntuforums.org/showthread.php?t=983808')] Go to your home directory and create a folder named "PDF" (all letters capitalized)

after doing so, and without further configuration, I was able to print to PDF!

The same can be done at the command line as follows:
1.- "sudo apt-get install cups-pdf"
2.- "mkdir ~/PDF"

note: I tried other options before doing as indicated above. One of them (as suggested by [aggiemarine07]('http://ubuntuforums.org/showpost.php?p=6216706&postcount=18')) was using this command:
"sudo chmod 0755 /usr/lib/cups/backend/*"
...not quite sure if it helped as well.

(remark: aggiemarine07 did not include sudo as part of the command, but if not present I hadn't permission to modify the files' attributes)

---

### Post by chmick on 2008-11-28
Finally solved. But i don't know how.
It seems a kernem update and i reboot solved the problem .
Thanks to all

Hy
It seems I have the same problem, even with the latest update. I can not print anything with the cups-pdf printer. 
I did the chmod 755 trick , change app armor configuration, but nothing work . 
here is my cupsd.conf and my cups-pdf.conf ? could you compare with yours (i m running intrepid on amd64).

cupsd.conf :
 LogLevel warning
SystemGroup lpadmin
# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
# Disable printer sharing and shared printers.
Browsing Off
DefaultAuthType Basic
<Location />
  # Restrict access to the server...
  Order allow,deny
</Location>
<Location /admin>
  Encryption Required
  # Restrict access to the admin pages...
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>


my cups-pdf.conf

#  cups-pdf.conf -- CUPS Backend Configuration (version 2.4.8, 2008-06-22)

### Key: Out

Out ${HOME}/PDF

#AnonDirName /var/spool/cups-pdf/ANONYMOUS

Label 0

### Key: AnonUser
##  user for anonymous PDF creation (this might be a security issue)
##  set this to an empty value to disable anonymous
### Default: nobody

#AnonUser nobody
### Key: AnonUMask
##  umask for anonymous output
##  these are the _inverse_ permissions to be granted
### Default: 0000

#AnonUMask 0000

### Key: UserUMask
##  umask for user output of known users
##  changing this can introduce security leaks if confidential
##  information is processed!
### Default: 0077

#UserUMask 0077

### Key: Grp
##  group cups-pdf is supposed to run as - this will also be the gid for all
##  created directories and log files
### Default: lp

Grp lpadmin
#Log /var/log/cups

### Key: LogType
##  log-mode 
##  1: errors
##  2: status (i.e. activity)
##  4: debug - this will generate a lot of log-output!
##  add up values to combine options, i.e. 7 is full logging
##  if logging is disabled these setting have no effect
### Default: 3

LogType 1


#GhostScript /usr/bin/gs

### Key: GSTmp
##  location of temporary files during GhostScript operation 
##  this must be user-writable like /var/tmp or /tmp ! 
### Default: /var/tmp

#GSTmp /var/tmp

#GSCall %s -q -dCompatibilityLevel=%s -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pdfwrite -sOutputFile="%s" -dAutoRotatePages=/PageByPage -dAutoFilterColorImages=false -dColorImageFilter=/FlateEncode -dPDFSETTINGS=/prepress -c .setpdfwrite -f %s

### Key: PDFVer
##  PDF version to be created - can be "1.5", "1.4", "1.3" or "1.2" 
##  MacOSX: for using pstopdf set this to an empty value
### Default: 1.4

#PDFVer 1.4

### Key: PostProcessing
##  postprocessing script that will be called after the creation of the PDF
##  as arguments the filename of the PDF, the username as determined by 
##  CUPS-PDF and the one as given to CUPS-PDF will be passed
##  the script will be called with user privileges
##  set this to an empty value to use no postprocessing
### Default: <empty>

#PostProcessing

---

