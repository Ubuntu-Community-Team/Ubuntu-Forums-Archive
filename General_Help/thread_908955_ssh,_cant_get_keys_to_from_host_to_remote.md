---
title: "ssh, cant get keys to from host to remote"
date: 2008-09-03
forum: General Help
---

### Post by adult swim on 2008-09-03
i am a complete noob when it comes to ssh.  on my host i have set up ssh as described here [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH) and im trying to get it to do a key based login only.  when im trying to import the keys from the host to the remote computer by ssh-copy-id -i ~/.ssh/id_rsa.pub aaron@192.168.1.103, i get the message "/usr/bin/ssh-copy-id: ERROR: No identities found."  if i go ahead and log into my host via password and then run ssh-copy-id -i ~/.ssh/id_rsa.pub aaron@192.168.1.103, it says ```
Now try logging into the machine, with "ssh 'aaron@192.168.1.103'", and check in:

  .ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.
```  i log in like the messages says and everything works fine, i am asked for my pass phrase, not the host computer password.  now if i exit out of all of the ssh tunnels i have opened, and try to login with ssh aaron@192.168.1.103 it is back to asking me for the host password, instead of the passphrase.  if i turn password authentication off in ssd_config and restart ssh when i try to login i get the error message Permission denied (publickey).  what am i doing wrong here?

---

### Post by cdtech on 2008-09-03
I noticed it failed to mention that you need to add:
> Once you login to your workstation computer, get a terminal window and run ssh-add. This will prompt you for your ssh passphrase and load your key for this session. Once this is done, you should be able to ssh into any other system that has the same authorization key without having to enter a password.

---

### Post by Mister.Vash on 2008-09-03
Can you try
```

ssh 192.168.1.103

```

and see if that works?  If not, post the response

---

### Post by adult swim on 2008-09-03
maybe to be more clear, when i log in, instead of asking me the password, i would like it to only prompt for the key passphrase.

---

### Post by adult swim on 2008-09-03
> **Mister.Vash said:**
> Can you try
```

ssh 192.168.1.103

```

and see if that works?  If not, post the response
when i try this, it returns huff@192.168.1.103's password: 
Permission denied, please try again.

---

### Post by Mister.Vash on 2008-09-03
Reading the thread again, it looks like you might not have generated a key on the source machine.

On your source machine, under you ~/.ssh folder do you have either a id_dsa.pub or a id_rsa.pub file?  If you don't you will need to generate one with the ssh-keygen program.  Then run the ssh-copy-id from the source machine as you did before

If you do have either, then copy whichever one you have to the destination machine ( do not overwrite the existing one on the destination machine! ), and then append the text from yours to the ~/.ssh/authorized_keys files

---

### Post by adult swim on 2008-09-04
one last question.  will i have to import the key files to every computer i plan on connecting to the server with?  i may have been misunderstanding the keys all along.  i thought that when i log on to the server from  a computer that doesnt have the ssh key on it, that it would prompt me for the key passphrase and sort things out itself.  is that not the way it works?

---

### Post by Mister.Vash on 2008-09-06
Yes, you will need to use the ssh-copy-id to get your ID to the other machines.  You just have to do that step the very first time you connect to set it up.  After that, you are using the key

---

