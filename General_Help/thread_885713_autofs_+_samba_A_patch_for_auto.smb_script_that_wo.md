---
title: "autofs + samba: A patch for auto.smb script that works"
date: 2008-08-10
forum: General Help
---

### Post by vmp on 2008-08-10
Hi,

I recently switched to ubuntu for desktop and I was quite disappointed that the
autofs auto.smb script coming with the package was not working.
I spent a few hours and managed to locate the problem and find a solution, so I would like to share it.

-------------------------------

**Problem**:
Even if you setup autofs & auto.smb to properly read credential files, it does not work.
```
$ ls /smb/host (works fine, listing the available shares on the host, but)

$ ls /smb/host/share (goes into an endless recursion returning the list of shares. e.g.:)

$ls /smb/host/share1
/smb/host/share1/share1
/smb/host/share1/share2
...

$ ls /smb/host/share1/share1
/smb/host/share1/share1/share1
/smb/host/share1/share1/share2
...
```

I found that the problem in the script **/etc/auto.smb**.
This executes the command **smbclient -gL** to get the list of shares for a host.
But the script passes $1 variable (named $key in the script) which is the full host/path part.
The result is that for every host/share path the command and the script returns the list of shares on the server
and not the subdirectories of the share as it should.

**Solution**:

**1. **First configure */etc/auto.master* to use auto.smb script. Here is mine:
```
#
# $Id: auto.master,v 1.4 2005/01/04 14:36:54 raven Exp $
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#/misc	/etc/auto.misc --timeout=60
/smb	/etc/auto.smb  --timeout=30
#/misc	/etc/auto.misc
#/net	/etc/auto.net
```
Note: Uncomment any other services you want to use and set the unmount timeout to your preferences


**2.** Authentication setup
You may want to use different username/password/domain per server or per smb share.
smbclinet allows you to provide the username/passowrd/domain from a file called the credentials file.
The format of this file is very simple:
```
username = <value>
password = <value>
domain   = <value>
```
The auto.smb script allows you one of the following options:
* A global credentials file for auto.smb, if not provided
* Looks for per share credentials file with the name *host.share* under the directory /etc/auto.smb.credentials
* If host.share file not found, looks for a file named as 'host' under /etc/auto.smb.credentials
Here is an example of how your /etc/auto.smb/credentials directory should look:
```
/etc/auto.smb.credentials/
      host1
      host2
      host2.share1
```
* When you invoke *ls /smb/host1/anyshare*, it will get credentials from /etc/auto.smb.credentials/host1
* When you invoke *ls /smb/host2/share1*, , it will get credentials from /etc/auto.smb.credentials/host2.share1
* When you invoke *ls /smb/host2/anyothershare*, , it will get credentials from /etc/auto.smb.credentials/host2


**3.** The */etc/auto.smb* script (make sure it is executable!):
```
#!/bin/bash

# $Id: auto.smb,v 1.3 2005/04/05 13:02:09 raven Exp $

# This file must be executable to work! chmod 755!

# IC patch
# The problem with the original file was that it was executing smbclient -gL $key
# But $key contains the full path e.g.: server/share/subdir
# This was causing auto.smb to go to an endless loop
# This modified file corrects this problem by passing just the host to smbclient
# and in addition it provides a simple method to locate the credentials file
# The changed parts are marked as "IC patch"
# Please read the creddir variable description to see how to provide credentials files
# Note: When you search for an inexistent share, or you authentication fails the script behaves the wrong way
#       This is because smbclient does protest, it just falls back like calling it
#       as smbclient -gL host
#       A check at the smbclient output should be done to avoid this, but I haven't figured it out yet
# Ioannis Chronakis <i.chronakis at gmail dot com>

key="$1"
mountopts="-fstype=cifs"
smbopts=""

# IC patch
# Look for credentials files under the creddir
# If $key is just the host name, then $credfile=$creddir/$host
# If $key is in the form of host/share,
# first look for a file $creddir/$host.$share
# and it does not exist, look for $creddir/$host
creddir="/etc/auto.smb.credentials"

# IC patch
# Providing a common credfile for everything, will override the above lookup method
credfile=

# IC patch
# The problem is that the key ($1) is the full path with the host
# So there should be one key for each directory
# To solve the problem:
# Easy: Get the first part of the $1 (/host/share/...)
# Comprehensive: Look the first two (host and share)
# If key does not exist, look just for the host
host=${key%%/*}
if [[ "$key" =~ '/' ]]; then
        path=${key#*/}
fi

if [ -z "$credfile" ]; then
	# Search for credentials file
	if [ -n "$path" ]; then
		if [[ "$path" =~ '/' ]]; then
			share=${path%%/*}
		else
			share=$path
		fi
	fi
	
	# First look for $creddir/$host.$share then for $creddir/$host
	if [ -n "$share" ]; then
		credfile="$creddir/$host.$share"
		if [ ! -e $credfile ]; then
			credfile="$creddir/$host"
		fi
	else
		credfile="$creddir/$host"
	fi
fi

for P in /bin /sbin /usr/bin /usr/sbin
do
	if [ -x $P/smbclient ]
	then
		SMBCLIENT=$P/smbclient
		break
	fi
done

[ -x $SMBCLIENT ] || exit 1

if [ -e $credfile ]; then
	mountopts="$mountopts,credentials=$credfile"
	smbopts="-A $credfile"
else
	smbopts="-N"
fi


# IC patch
# Do not browse for $key, just the host part
$SMBCLIENT $smbopts -gL $host 2>/dev/null| awk -v key="$host" -v opts="$mountopts" -F'|' -- '
	BEGIN	{ ORS=""; first=1 }
	/Disk/	{ if (first) { print opts; first=0 }; sub(/ /, "\\ ", $2); print " \\\n\t /" $2, "://" key "/" $2 }
	END 	{ if (!first) print "\n"; else exit 1 }
	'

```


**4.** Restart autofs
You will need to restart your autofs daemon
```
sudo /etc/init.d/autofs restart
```


**5.** Accessing the samba shares
auto.smb will not automatically list servers under /smb.
You have to refer to them via any filesystem operation.
e.g.: ls /smb/host
This will automount the hosts shares under /smb/host

One solution will be to setup symlinks from your home directory, but be careful, when doing ls in the directory with the symlinks it will mount all the targes and this may slow down listing your directory. Better solution is to put symbolic links like those under a subdirectory.

e.g. $HOME/smb/link_to_host

**6.** Limitations
The script will go back to the infinite recursive behavior in the following cases:
* You try to access an inexistent share. It will list the existing shares as directory contents
* You provided wrong username or password
* The credentials file does not exist or it is not accessible

-----------------------------------

I hope this helped.

IC

---

### Post by Tech Wrangler on 2008-08-15
This is precisely the problem I've been grappling with for the past day.  Thanks for posting your work.

Unfortunately, I still can't get it to work. I still have the recursive directory strangeness.  I also tried [this other solution]("http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs") I stumbled upon, but it does the same thing. 

My problem might be that my shares are not password protected.  I have tried various methods of creating the credentials file (blank file, variable names listed but blank, variable names with filler)  but all of them result in the same outcome.

Something is happening, as I can see /smb/host and /smb/host/share/ but then it's just /smb/host/share/share/share/... 

Any aid would be appreciated, Thanks!

---

### Post by vmp on 2008-08-15
Hi,

I didn't know you can have non password protected shares! 
Is it possible that you actually need to have a user name with an empty password? To my knowledge windows and default samba configuration do not allow the guest user. You may not need a password but you need to have a valid account with access rights to the share.

You get the behaviour you describing when:
* smbclient called by auto fails to authenticate (wrong username/password, no access to the share)
* the share or directory name does not exist

To troubleshoot this you can do the following:

1. Try to access the share you want by using smbclient. Do you get access to the share e.g.: list it's contents or copy something. Record the options. Note, that smbclient uses by default your linux username which may be the same with your windows share username

2. If you can access your shares with smbclient, next step is to manually use mount.cifs or mount.smbfs to get the mount options right. Play with username= and password before using credential file instead

3. After you manage to manually do a mount.cifs and get normal access to the share, test the /etc/auto.smb script. This is easy since it is a normal bash script. The usage is
/etc/auto.smb host/share/dir

I hope the above will be of help

---

### Post by Tech Wrangler on 2008-08-15
Thanks for your prompt response.  Indirectly, you have provided me with the solution!

Using smbclient I could access the files, just as I could through nautilus.  But when I tried using mount.smbfs, I was told I didn't have the package.  I was sure I had all the samba packages, but I guess I was wrong.  Installed, and *voila*!  Your script works perfectly!  

Thanks again.  Now my wife won't need my assistance to access our photo directories.

---

### Post by Tech Wrangler on 2008-08-15
BTW, in Hardy sharing is as easy as it is in XP, and it's possible to allow unrestricted access (though there are a few file ownership issues).  Just right click on the folder in nautilus.  If you have a firewalled home network, this is all you need.  Well... that and the ability to access the files seamlessly...

---

### Post by vmp on 2008-08-15
Glad to be of help, even indirectly!

This sounds like a dependency problem. I think the auto.smb should check to see if there is the mount.smbfs is present and report it to syslog.

Indeed very easy to share files from nautilus. I very recently switched to ubuntu as my desktop and haven't found all the goodies yet, thanks for the tip :)

---

### Post by hobie on 2008-12-22
Thanks a lot for this posting. I have spent several hours trying to figure out what was wrong with my autofs.  This fix did the trick.

---

### Post by EnlistedSquire on 2009-05-08
Hi, I set up autofs successfully using this modified version of auto.smb when I upgraded to 8.10 (the upgrade from 8.04 broke my existing set up).

I'm now trying to get it working on a new install of 9.04 but, despite copying all the autofs config files from my installation of 8.10 I can't get it to work. Has anyone else had trouble with upgrading to 9.04?

I have the shares configured to mount in /mnt/Network/[share]. Autofs is creating the /mnt/Network directory but nothing below it.

I'm currently in the process of backing up my working 8.10 installation and then I'm going to do a distribution upgrade on it to see if autofs stops working in that case, at least then I might be able to narrow down where the problem lies.

---

