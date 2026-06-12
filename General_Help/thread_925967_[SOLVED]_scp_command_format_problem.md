---
title: "[SOLVED] scp command format problem?"
date: 2008-09-21
forum: General Help
---

### Post by MrGrey1 on 2008-09-21
Hi,
trying to use scp to connect to a non default port and not having any luck, it keeps trying to connect on port 22 despite me using -P to specify another port, can someone tell me where I'm going wrong in my command please?

$ > scp -v -2 -i ~/.ssh/masterkey -P54321 [email]SERVERUSER@***.***.***.***:/home/UN/.bash[/email]_aliases UN@***.***.***.***:/home/UN/Desktop/

Executing: /usr/bin/ssh '-v' '-x' '-oClearAllForwardings yes' '-n' '-l' 'SERVERUSER' '***.***.***.***' 'scp -v' '/home/UN/.bash_aliases' 'UN@***.***.***.***:/home/UN/Desktop/'
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to ***.***.***.*** [***.***.***.***] port 22.

As you can see, I tried port 54321 and it tries connecting on port 22?
Any ideas?

Thx.

---

### Post by Mister.Vash on 2008-09-21
From your debug output, the **-oClearAllForwardings yes** is the issue.  The is going to prevent the port forwarding that you are trying to do.

Take a look and see if this option has been set in your /etc/ssh/ssh_config
Also, did you create a config file under your ~/.ssh/ directory?  If you did, check that file as well.


Once you find it, comment the option out
# ClearAllForwardings yes

---

### Post by MrGrey1 on 2008-09-21
> **Mister.Vash said:**
> From your debug output, the **-oClearAllForwardings yes** is the issue.  The is going to prevent the port forwarding that you are trying to do.

Take a look and see if this option has been set in your /etc/ssh/ssh_config
Also, did you create a config file under your ~/.ssh/ directory?  If you did, check that file as well.


Once you find it, comment the option out
# ClearAllForwardings yes

Hi Mister.Vash, thanks for the quick reply.
I checked /etc/ssh/ssh_config, it's still default and there's no option there re ClearAllForwardings yes. I tried adding the option and setting it to no but it made no difference. I don't have a ~/.ssh config file either. I also tried adding '-oClearAllForwardings no' to the command but it gave me an error 'command-line line 0: Missing yes/no argument.'
So I then tried '-oClearAllForwardingsno' and the command executed the same as it did initially... anywhere else this setting may be hiding?
I had a hunt around on google for similar issues but didn't find anything. All I found was references to the same files you mentioned...

Here's my ssh_config


# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

---

### Post by Mister.Vash on 2008-09-21
Can you try the scp command with the -vvv option instead of the -v option?  That should produce a more verbose output and include the locations of the configuration files being used.

---

### Post by MrGrey1 on 2008-09-21
> **Mister.Vash said:**
> Can you try the scp command with the -vvv option instead of the -v option?  That should produce a more verbose output and include the locations of the configuration files being used.

$ > scp -vvv -2 -i ~/.ssh/masterkey -P 54321 [email]SERVERUSER@***.***.***.***:/home/SERVERUSER/.bash[/email]_aliases UN@***.***.***.***:/home/UN/Desktop/
Executing: /usr/bin/ssh '-v' '-x' '-oClearAllForwardings yes' '-n' '-l' 'SERVERUSER' '***.***.***.***' 'scp -v' '/home/SERVERUSER/.bash_aliases' 'UN@***.***.***.***:/home/UN/Desktop/'
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to ***.***.***.*** [***.***.***.***] port 22.


Unfortunately it appears there's no difference. The configuration appears to be executed before the /ssh/ssh_config file is read, ie Executing: /usr/bin/ssh...

---

### Post by Mister.Vash on 2008-09-21
Can you check grep your aliases and set output to see if something is being added to your scp command?  Can you also run a 'which scp' command?


I did a test on mine - could you do the following on yours?
```

touch testfile
scp -vvv testfile test:destination

```
It just creates an empty file and tries to do the file transfer to a fake destination.  I just want to see what your output is as a comparison.

This was the output on mine:
scp -vvv testfile test:destination
Executing: program /usr/bin/ssh host test, user (unspecified), command scp -v -t destination
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
ssh: test: Name or service not known
lost connection

---

### Post by Mister.Vash on 2008-09-21
One other thing - Just to verify are you copying between two remote hosts?  If you are what happens if you use your machine as an intermediary?  Can you successfully pull a small file to your machine and put it back on the other system?

---

### Post by MrGrey1 on 2008-09-22
Nothing in my aliases.

$ > which scp
/usr/bin/scp

$ > scp -vvv testfile test:destination
Executing: program /usr/bin/ssh host test, user (unspecified), command scp -v -t destination
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
ssh: test: Name or service not known
lost connection


I think you've found where I'm going wrong;
"Just to verify are you copying between two remote hosts?"
I'm not actually, I'm trying to copy to the machine I'm on. Realized this and removed the destination machine from the command and now get;

 scp -v -2 -P54321 [email]SERVERUN@***.***.***.***:/home/SERVERUN/Desktop/SCRAP.txt[/email]
usage: scp [-1246BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
           [-l limit] [-o ssh_option] [-P port] [-S program]
           [[user@]host1:]file1 ... [[user@]host2:]file2

So it appears the command is not correct at all?

Is the command for an ssh encryption file supposed to be
-i ~/.shh/keyfile    or
-o IdentityFile=~/.ssh/keyfile     ?

Thanks for your help Mister.Vash.

---

### Post by Mister.Vash on 2008-09-22
You don't need to specify the identity file if you are using the default one that is in your ~/.ssh/ folder. If you do need to specify it, use the -i ~/.ssh/whateveryourkeyfileisnamed

OK, try this, it will copy a file from the server to your local machine

scp -v -2 -P54321 [email]SERVERUN@***.***.***.***:/home/SERVE...ktop/SCRAP.txt[/email] ~/

And just to make to make sure we are talking about the same thing
the -v is verbose
the -2 is ssh protocol 2
the -P54321 specifies to use port 54321 on the remote machine
the SERVERUN is the name of the account on the source server
the ***.***.***.*** is your source IP
the /home/SERVE...ktop/SCRAP.txt is the file that your are reading
and the ~/ is the destination of your home folder

and if you want to copy a file to the server, you would do:
scp -v -2 -P54321 ~/Desktop/file.txt [email]SERVERUN@***.***.***.***:/home/SERVE...ktop[/email]/

---

### Post by MrGrey1 on 2008-09-23
Awesome:

debug1: Exit status 0


Thanks, successfully copied with encryption key and all.

---

