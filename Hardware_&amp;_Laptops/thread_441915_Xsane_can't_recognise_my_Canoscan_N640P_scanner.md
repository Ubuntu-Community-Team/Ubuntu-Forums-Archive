---
title: "Xsane can't recognise my Canoscan N640P scanner"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by Buster95 on 2007-05-13
When I invoke Applications/Graphics/XSane Image Scanner, I get a message "No devices available".
When I invoke "scanimage" in a terminal, the scanner buzzes for a while and the terminal fills up with all sorts of gobbledegook, but no scan.
I have enabled canon_pp in /etc/sane.d/dll.conf by removing the "#" in the appropriate places.
When I "scanimage -L", I get the message "device 'canon_pp:parport0' is a CANON N640P flatbed scanner", so presumably it can see it.

Any advice or next steps?

---

### Post by lacis_alfredo on 2007-05-19
Found similar thing that scanimage works for root, but fails for normal users.

Under root, scanimage reports:
"Options specific to device `canon_pp:parport0':"

But fails for normal users.

I also found that there is no device called:
/dev/parport0

How do I unf*ck this stupid name mangling (`canon_pp:parport0') that seems to have crept into Linux?  (you see it has crept into things like browsers with "about:config", but this doesn't tell you where the relevant file(s) are)

This is just another level of obfuscation that stops people in their tracks.

<rant>
I'm guessing that someone thought "Hmm, I don't like /dev/xxxxx. Instead I'll call it 'my_secret_society_name:xxxxx'.  Oh, and I won't tell anybody where the file is, how to list them, how the link is made, or how to unmangle the name or link.    He, he, he..."

This hiding of information that is happening more often with every new distro of Linux seems to have the heavy hand of Microsoft behind it.  Are Microsoft's agents getting into developer forums and obfuscating everything that they can get their hands on?   It sure seems like it.
</rant>

DON'T HIDE THINGS, PEOPLE!  
IF YOU HAVE A CRAZY NAME, PUT THE REAL NAME NEARBY (NEXT LINE, PARENTHESES, ETC).  WHATEVER IT IS, SHOW IT, & SHOW IT *NOW*!

In General Semantics, for sanity's sake, you have to tell others what your sources are, including things like names, dates, authorities, etc.  

Hiding things just creates insanity.   ](*,)

---

### Post by Dave Coulstock on 2007-06-27
I have the same problem.  It's to do with the permissions of the /dev/parport0 device file.  You can run the scanner with Xsane/Sane as root user but this is not recommended.  The device file has ownership root/lp and permissions owner & group can read/write but others can only read.  As root user try changing the ownership to root/users - from the command line "chown root:users /dev/parport0" and then as normal user invoke xsane.
The device file appears to be set up/reset at boot time so its ownership reverts to root/lp.  I am looking for a way of issuing the chown command at boot time and have tried putting it in the "dummy" shell script /etc/rc.local.  This seems to work but not immediately at startup, sometime after the system is running.  Presumably rc.local is called by some process after boot is complete.

Let me know if this helps.

Dave.

---

### Post by Buster95 on 2007-06-27
> **Dave Coulstock said:**
> I have the same problem.  It's to do with the permissions of the /dev/parport0 device file.  You can run the scanner with Xsane/Sane as root user but this is not recommended.  The device file has ownership root/lp and permissions owner & group can read/write but others can only read.  As root user try changing the ownership to root/users - from the command line "chown root:users /dev/parport0" and then as normal user invoke xsane.
The device file appears to be set up/reset at boot time so its ownership reverts to root/lp.  I am looking for a way of issuing the chown command at boot time and have tried putting it in the "dummy" shell script /etc/rc.local.  This seems to work but not immediately at startup, sometime after the system is running.  Presumably rc.local is called by some process after boot is complete.

Let me know if this helps.

Dave.

Thanks Dave,
I'll give it a try and report back.
Cheers

---

### Post by Buster95 on 2007-06-28
> **Dave Coulstock said:**
> I have the same problem.  It's to do with the permissions of the /dev/parport0 device file.  You can run the scanner with Xsane/Sane as root user but this is not recommended.  The device file has ownership root/lp and permissions owner & group can read/write but others can only read.  As root user try changing the ownership to root/users - from the command line "chown root:users /dev/parport0" and then as normal user invoke xsane.
The device file appears to be set up/reset at boot time so its ownership reverts to root/lp.  I am looking for a way of issuing the chown command at boot time and have tried putting it in the "dummy" shell script /etc/rc.local.  This seems to work but not immediately at startup, sometime after the system is running.  Presumably rc.local is called by some process after boot is complete.

Let me know if this helps.

Dave.

Hello Dave, Tried your suggestion without success. Any other ideas?
Cheers

---

### Post by Dave Coulstock on 2007-06-28
Hi,

I assume you managed to change the ownership of the parport0 device file.  When you retried xsane from your normal user id what response (messages) did you get?  If you got the "no devices available" message again it could be that your user id is not in group users, although this is unlikely. If this is the case try changing the ownership group to your user group using the chown command : "chown root:uuu /dev/parport0" (uuu=your user group).  Another option would be to change parport0's permissions so that other users can read & write - use command "chmod  o+w /dev/parport0" as root user.  
Both these changes will be reset on a reboot.  I have put the chown command in the /etc/rc.local script so that the change is made automatically just after boot up.
If the above doesn't work try adding your user id to the lp group.   
Let me know how you get on - all details which you think might help.

---

### Post by Buster95 on 2007-07-21
Hello again,
I followed your instructions in root. No messages came up to indicate that I was unsuccessful. Then changed to a user terminal and tried to invoke xsane again. Same response "No device available".
This has me stumped.
Cheers

---

### Post by Dave Coulstock on 2007-07-24
Hi,
To recap from your earlier posts : XSane & Sane are installed and the scanner is configured since "scanimage -L" gives "device 'canon_pp:parport0' is a CANON N640P flatbed scanner".

In a shell console type "ls -l /dev/parport0".  This will probably display "  crw-rw---- 1 root lp 99, 0 2007-07-24 18:50 /dev/parport0".  This shows that the device file parport0 is only readable by root and members of the group lp.  You need to add your user name, or the name of the user from which you want to access the scanner, to the group lp. 
 
In the console type "gpasswd -a username lp" to add the desired user to group lp  - you will need to be root user to do this.  You should see the response "Adding user username  to group lp".

Now  launch xsane from that user.  If all is well it should find your scanner.  This change is permanent and will remain effective through restarts of the system.

Dave.

---

### Post by mcmilner on 2007-08-16
Dave, I have a very similar problem but your answer still does not help me do you have any other suggestions?

I have an Epson Perfection 1200S scsi scanner that appears to work fine from the terminal as root but if I go Applications>Graphics>Xsane I get "no devices available". For example:

[INDENT]sudo scanimage -L
device `epson:/dev/sg2' is a Epson Perfection1200 flatbed scanner
device `epkowa:/dev/sg2' is a Epson Perfection 1200 flatbed scanner[/INDENT]

and other root scanning commands operate the scanner.  And "ls -l /dev/parport0" gives:

[INDENT]crw-rw--w- 1 root users 99, 0 2007-08-16 17:58 /dev/parport0[/INDENT]

so I don't think this is a problem and I tried your changes above anyway.

Do you have any more ideas? thanks.

---

### Post by philinux on 2007-08-16
My epson perfection 2480 will only activate if I run sudo xsane from terminal.

Also under "manage groups" the group LP is not shown how come?](*,)

---

### Post by Dave Coulstock on 2007-08-22
Hi MC,

The "no devices available" message gives 6 possible reasons for failure, the most likely of which is "the permissions of the device file do not allow you to use it - try root".  The output from the "scanimage -L" command indicates that your device file is /dev/sg2 since yours is a scsi scanner (not /dev/parport0 which it is with my parallel port device).  Run the  "ls - l /dev/sg2) command to see the user/group for this file.  Then add your userid to this group using the "gpasswd -a userid groupname" command.  If the group is "users" - as it is for /dev/parport0 - then the scanner still will not work from this userid and we will have to look elsewhere for the solution; otherwise it should work. Let me know how you get on.

Dave. 

Ps. for technical info see man pages sane-epson and sane-scsi  (type "man sane-epson" and "man sane-scsi" in a terminal). 

Phil,

I assume that you get the "no devices available" message when you run xsane as a normal user.  Again it's probably a device file permissions problem.  Your scanner is a usb device so the device file will be something like /dev/usbscanner or /dev/usb/scanner.
Run the command "scanimage -L" as root user in a terminal to show the scanner and device file.  Then display the device file with the command "ls -l devicefilename"  to show the owner and group.  Add your userid to that group with the command "gpasswd -a userid groupname" (as root).  With luck your scanner should work from your normal user id.

I don't know why the lp group does not show under manage groups (I use Kubuntu and it does there); however running the gpasswd command is easy enough.

Let me know if this works - my scanner is not usb so I can't check this out.

Dave.

Ps. technical info: see man pages sane-snapscan and sane-usb.

---

### Post by mcmilner on 2007-08-23
Hi dave,

The result of the "ls - l /dev/sg2" command is:

[INDENT]crw-rw---- 1 root root 21, 2 2007-08-19 14:22 /dev/sg2[/INDENT]

I then did: "sudo gpasswd -a *my-userid* root"

and it said : "Adding user *my-userid* to group root"

XSane still won't work from the Applications menu. Do I need to reboot or something?

Sorry if these are dumb questions but I am very new to Linux and there is a lot to learn.

Thanks for your time.

Nick

---

### Post by Dave Coulstock on 2007-08-23
Hi Nick,

You will have to log out and in to bring the change to your userid into effect; then xsane should work.  However I did not expect /dev/sg2 to have group root and adding your userid to this group confers root privileges on your userid.  This can be dangerous and could lead to system damage if you inadvertently make mistakes while using the system.  This is the reason for the warning message when you run xsane as root.  Therefore I would advise you to remove your userid from group root - run command "gpasswd -d userid root" as root.  Sorry for this but with my parallel port scanner /dev/parport0 has owner root and group lp.

A safer approach to the problem in this case is to change the group for /dev/sg2 to "scanner" using the command "chown root:scanner /dev/sg2" and then add your userid to this group using command "gpasswd -a userid scanner". Run both commands as root.  After logging off /on (but don't reboot) you should be able to run xsane  from your userid.  The change to your userid is permanent but that to /dev/sg2 is not and will revert when you reboot.  One way to make this "permanent" is to put the command into the "rc.local" shell script which is in the /etc directory and is run every time the system is booted.  I will try to explain how you can do this in another post tomorrow (it's getting late now!).  In the meantime I would suggest you remove your userid from root and try the second approach.

Regards,

Dave.

---

### Post by mcmilner on 2007-08-24
Dave,

All the above worked just how you said it would. I would appreciate  your instructions on making the change permanent.

Best, Nick

---

### Post by Dave Coulstock on 2007-08-26
Hi Nick,

I little later than I had hoped but here's a method of making the change to /dev/sg2 permanent.  This involves changing the script rc.local which is invoked at startup time and  resides in /etc directory.  The method is all command line and I assume you are familiar with using a full-screen editor.  

1. From the desktop select  Applications->System Tools->Konsole

2. Enter the following commands (in order) to create a backup copy of rc.local in your home directory and also to create a version with the "chown" command for the /dev/sg2 device file. 
cp /etc/rc.local ~/              : copies file to your home directory
ls -al rc.local                     : check that file has been copied
mv rc.local rc.local.backup  : rename to backup copy
cp /etc/rc.local ~/              : repeat 1st command to get copy to amend
gedit rc.local                     : edit the file
 
3. In the editor insert 2 lines immediately after the comment line "# By default this script does nothing.";  the 1st line will be a comment, the 2nd the chown command ...

# Change ownership of /dev/sg2 device file to enable non-privileged users to run Xsane.

chown root:scanner /dev/sg2

You can type or cut and paste these into the file.  The comment can, of course, be whatever you like!    
Save the changes and then quit.

4. sudo cp -i rc.local /etc  : copy the edited file to the /etc directory to replace the version there - you will be asked to enter your password.  Then reply Y  to the question "cp: overwrite /etc/rc.local ?".

5.  Check that the new version is in place ...
ls -al /etc/rc.local   : the timestamp should show the time of the copy
less /etc/rc.local    : will display the contents of the file; enter q to exit less.

6.  Close the konsole session and reboot.

Once you've signed on you should be able to invoke xsane.  You can check the ownership of /dev/sg2 with the  command ls -al /dev/sg2 from a konsole.

Let me know how this goes and if there is anything that requires further explanation.  You can of course achieve most of the above without recourse to the command line but I think using the latter helps to a better understanding of  the system.

Regards,

Dave.

Ps.  I can recommend  a couple of little books which you may find helpful with the command line approach ...

1. Linux Pocket Guide by Daniel J Barrett (pub. O'Reilly)
2. Linux Phrasebook by Scott Granneman (pub. Sams)

Both are inexpensive, especially via Amazon!

---

### Post by mcmilner on 2007-08-26
Dave,

Thanks for the tutorial. Again, it all worked just as you said.

I have the Pocket Guide book by Barrett and I am slowly working through it and the Ubuntu Bible.  I have got quite a few things sorted out and working it is just that without the background knowledge  I sometime don't know where to start to fix something.

Regards and thanks.

Nick

---

