---
title: "[SOLVED] ssh with no password?"
date: 2008-07-31
forum: General Help
---

### Post by jerome1232 on 2008-07-31
I wrote this backup script for my teamspeak server
```
#!/bin/bash
#backsup teamspeak server locally and on remote machine
date=$(date +%m%d%Y)
cd /home/teamspeak/tsbackup/
#create a local archive and a list of the archive contents
tar cvvjf tssbackup-$date.tar.bz2 --exclude tsbackup ~/ > tssbackup-$date.list
#remove old backups
find tssbackup* -atime +6 | xargs rm
echo Local backup finished

#now repeating process on desktop computer
tar cf - --exclude tsbackup ~/ | ssh jeremy@desktop "cd backup/tssbackup ; tar xpf - ; tar cvvjf tssbackup$date.tar.bz2 home/ > tssbackup$date.list ; find tssbackup* -atime +6 | xargs rmf ; rm -rf home/"
echo Remote backup finished
```

obviously I'm going to need to be able to ssh from the server to my desktop with no password, following [this]("https://help.ubuntu.com/community/SSHHowto") URL doesn't seem to work.

I am copying a key located at
/etc/ssh/ssh_host_rsa_key.pub on the server
to
~/.ssh/authorized_keys on the desktop
restart ssh on desktop with
sudo /etc/init.d/ssh restart

and it's still prompting me for password, I'm not sure what to change here.

---

### Post by Dr Small on 2008-07-31
Make sure in your /etc/ssh/sshd_config file, you have this stuff set:
```
PubkeyAuthentication yes
AuthorizedKeysFile	.ssh/authorized_keys
PasswordAuthentication no
```

Then restart the server and try.

---

### Post by geirha on 2008-07-31
That's the host-key. You need to create a key-pair for the user. You can do this with ```
ssh-keygen -t dsa    # save it to the default location, and you might need to set an empty passphrase
cat ~/.ssh/id_dsa.pub | ssh jeremy@desktop "cat >>.ssh/authorized_keys"
ssh-add              # load the key into the agent
ssh jeremy@desktop   # this should now be password-less

```

---

### Post by jimv on 2008-07-31
Also, on the server in /etc/ssh/sshd_config, make sure that 'HostbasedAuthentication' is set to 'yes', like 'HostbasedAuthentication yes'.

Then restart your ssh server and try logging on again.

---

### Post by jerome1232 on 2008-07-31
> **geirha said:**
> That's the host-key. You need to create a key-pair for the user. You can do this with ```
ssh-keygen -t dsa    # save it to the default location, and you might need to set an empty passphrase
cat ~/.ssh/id_dsa.pub | ssh jeremy@desktop "cat >>.ssh/authorized_keys"
ssh-add              # load the key into the agent
ssh jeremy@desktop   # this should now be password-less

```

Ok so I followed these steps and haven't made any changes to my sshd_config file.

```
tss2:~$ssh-keygen -t dsa
tss2:~$ cat ~/.ssh/id_dsa.pub | ssh jeremy@192.168.1.4 "cat >.ssh/authorized_keys"  # I had already slapped a key in here and wanted to delete what I had already put in.
tss2:~$ssh-add
Could not open a connection to your authentication agent.
      # well I tried to ssh in anyways
tss2:~$ ssh jeremy@192.168.1.4
Linux ubuntu 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
No mail.
Last login: Thu Jul 31 12:06:21 2008 from 192.168.1.3

```
ah, didn't ask for a password :)
Thanks looks like I was just fishing in the wrong area's for a key that didn't exist yet. I'm not sure what that error with ssh-add is all about (I'm ssh'd into the server, while doing all this)

I'm guessing those steps to edit sshd_config would disable password login entirely? I will try those on the server but the desktop should be fine, it's ssh port isn't open to the internet (ufw and router) and will be moved to a random port here soon.

---

### Post by geirha on 2008-07-31
> **jerome1232 said:**
> 
Thanks looks like I was just fishing in the wrong area's for a key that didn't exist yet. I'm not sure what that error with ssh-add is all about (I'm ssh'd into the server, while doing all this)


If i remember correctly, ubuntu used to run an ssh-agent, which you would use ssh-add to add keys to. Seems gnome has taken over that task now and made it slightly easier :)

EDIT: The above commands can be done through GUI too btw. Applications -> Accessories -> Passwords and Encryption Keys

---

### Post by jerome1232 on 2008-08-01
Actually this computer has no xserver, it sits in my closet and I access it using ssh. (so I don't think the ssh-add error was a new gnome thing, just not needed anymore)

---

