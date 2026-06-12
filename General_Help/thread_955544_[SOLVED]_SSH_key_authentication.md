---
title: "[SOLVED] SSH key authentication"
date: 2008-10-22
forum: General Help
---

### Post by porchrat on 2008-10-22
Hi all.

I am attempting to create a SSH connection (right now I am just testing it between two machines in my LAN).

I can't seem to get them to use RSA authentication properly.  I have a public RSA key stored in ~/.ssh/foo/bar

I have this in the sshd_config file:

```
HostbasedAuthentication no
```
and
```
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/foo/

```

When I attempt to connect from the client I get this ouput:

```
Permission denied (publickey,password)
```

I also have password authentication set to "no" on both sides because from what I have read when password authentication is set to "yes" it does password authentication and not key authentication.  Is this correct?

Anyone have some ideas for me?

---

### Post by No-Neck on 2008-10-22
Are you trying to point your sshd to the id_rsa.pub key file? This is how I set my server up:

```
cat ~/.ssh/id_rsa.pub >> authorized_keys
chmod 600 authorized_keys
```

And then in sshd_config:

```
AuthorizedKeysFile      %h/.ssh/authorized_keys
```

---

### Post by porchrat on 2008-10-22
> **No-Neck said:**
> Are you trying to point your sshd to the id_rsa.pub key file? This is how I set my server up:

```
cat ~/.ssh/id_rsa.pub >> authorized_keys
chmod 600 authorized_keys
```

And then in sshd_config:

```
AuthorizedKeysFile      %h/.ssh/authorized_keys
```

Yes it is pointing to authorized_keys and under that is indeed id_rsa.pub

---

### Post by porchrat on 2008-10-22
Could you do me a favour and check who the owner and group are in your ~/.ssh/authorized_keys directory is?

mine is root:root maybe that is the problem, but I doubt it as it should just be checking regardless.  Also do you put the id_rsa.pub under the home directory of the user you are remote logging in as, or can it go anywhere.  I assumed that the "%" in the sshd_config file meant you could have it anywhere.

---

### Post by No-Neck on 2008-10-22
Authorized_keys is not a directoy, it is a file containing the hash of id_rsa.pub.

Anyway, all these files are owned by my user on my server, however I can still log in as root if I allow the option in sshd_config.

---

### Post by mschutte on 2008-10-22
If you are trying to authenticate via rsa keys only, you need to disable the UsePam option in your sshd_config file. If not disabled it will always tryto authenticate using passwords.

---

### Post by porchrat on 2008-10-22
OK discovered that I was being a serious moron.  I created authorized_keys as a directory and then placed id_rsa.pub under authorized_keys.  So I corrected that and use cat to move the contents of id_rsa.pub into ~/.ssh/authorized_keys unfortunately that still hasn't helped.



Here is another thought.  As I mentioned previously the client machine returns this:

```
Permission denied (publickey,password).
```

If I have told the stupid thing this:

```
PasswordAuthentication no
```

in the config file.  Why is it still using a password?  Surely it should merely be using the authentication via key method?

---

### Post by No-Neck on 2008-10-22
As mschutte mentioned, change UsePam to no, I think it's right at the bottom.

Just to make sure: you've now pointed sshd to the authorized_keys file **and** restarted ssh? Not to be patronising, I always forget to do stuff like that. heh

---

### Post by porchrat on 2008-10-22
Yet another update.  Realised that my "PasswordAuthentication no" line was commented out in the sshd_config file on the server.

So now all I get is this:

```
Permission denied (publickey)
```


Suggestions anyone?  Please don't be shy I could really use the help:(

---

### Post by mschutte on 2008-10-22
Another trick you can try is to copy the rsa public keys to the two computers want to access using the ssh-copy-id command. The syntax is like this:

ssh-copy-id /root/.ssh/id_rsa.pub root@hostname

Hope this will solve your issue!!

---

### Post by porchrat on 2008-10-22
To clarify I generated the keys using this command:

```
ssh-keygen -t rsa
```

I then allowed it to send them to create them in the default location (~/home/.ssh) and copied the .pub across to the server.  I don't see a problem...maybe I should just try and generate new keys?

---

### Post by No-Neck on 2008-10-22
I can only get the (publickey) error when I move my id_rsa file out of my home/.ssh/ folder on my client. You're sure you're pointing it to the correct file?

---

### Post by porchrat on 2008-10-22
> **mschutte said:**
> If you are trying to authenticate via rsa keys only, you need to disable the UsePam option in your sshd_config file. If not disabled it will always tryto authenticate using passwords.

gave it a try, didn't work.  However as I mentioned previously I managed at least to stop it asking for passwords.

Sorry about that No-Neck and mschutte I didn't notice your posts earlier

---

### Post by porchrat on 2008-10-22
> **No-Neck said:**
> I can only get the (publickey) error when I move my id_rsa file out of my home/.ssh/ folder on my client. You're sure you're pointing it to the correct file?

Yup...at least I think I am:

```
IdentityFile ~/.ssh/id_rsa
```

There are two other lines above and below that one, one pointing to ~/.ssh/id_dsa and one pointing to ~/.ssh/Identity but they are both commented out

---

### Post by mschutte on 2008-10-22
This command is correct. It will generate a private and a public key in the .ssh folder in your user's home directory. As I mentioned earlier try to copy the pub key to the other host using the ssh-copy-id command and see if that solves your problem.


> **porchrat said:**
> To clarify I generated the keys using this command:

```
ssh-keygen -t rsa
```

I then allowed it to send them to create them in the default location (~/home/.ssh) and copied the .pub across to the server.  I don't see a problem...maybe I should just try and generate new keys?

---

### Post by porchrat on 2008-10-22
> **mschutte said:**
> This command is correct. It will generate a private and a public key in the .ssh folder in your user's home directory. As I mentioned earlier try to copy the pub key to the other host using the ssh-copy-id command and see if that solves your problem.

It returns this:

```
ssh: /root/.ssh/id_rsa.pub: Name or service not known
```

I also tried replacing "root" with /home/username_containing_.ssh but I received the same ouput.

Correct me if I'm wrong, but that is not a good sign.

Or at least, it doesn't seem good.

---

### Post by mschutte on 2008-10-22
Apologies, I should have clarified. When you execute the command it will most likely be as the user you are logged in as. For the purpose of clarity I will assume that you user name is porchrat.

You executed the *ssh-keygen it rsa* command as porchrat, hence the private and public keys are in /home/porchrat/.ssh folder.

You now issue a command similar to this one for the pc you want to ssh to using just the rsa keys:

ssh-copy-id /home/porchrat/.ssh/id_rsa.pub username@hostname

Just remember that when you generated the rsa keys it asked you to enter a passphrase. You will be challenged with this passphrase when you ssh to the remote host.


> **porchrat said:**
> It returns this:

```
ssh: /root/.ssh/id_rsa.pub: Name or service not known
```

I also tried replacing "root" with /home/username_containing_.ssh but I received the same ouput.

Correct me if I'm wrong, but that is not a good sign.

---

### Post by mschutte on 2008-10-22
Geez, sorry guys sometimes my brain is faster than my typing skills. The command should have read: *ssh-keygen -t rsa*

---

### Post by porchrat on 2008-10-22
> **mschutte said:**
> Geez, sorry guys sometimes my brain is faster than my typing skills. The command should have read: *ssh-keygen -t rsa*

I'm a little confused here lol

---

### Post by mschutte on 2008-10-22
I made a typo in my previous post. The message went something like ssh-keygen _it_ rsa. It should have read ssh-keygen -t rsa. Anyway did you manage to solve your ssh connection or is it still haunting you?

> **porchrat said:**
> I'm a little confused here lol

---

### Post by porchrat on 2008-10-22
> **mschutte said:**
> I made a typo in my previous post. The message went something like ssh-keygen _it_ rsa. It should have read ssh-keygen -t rsa. Anyway did you manage to solve your ssh connection or is it still haunting you?

still haunting me...I actually got distracted so I haven't advanced I tried using the ssh copy using the name of the user in place of root...still got that same response.  I pointed it to where id_rsa.pub is, but still...

---

### Post by mschutte on 2008-10-22
I just went back and re-read the entire post just to make sure we didn't miss something somewhere. I just have to clarify two things. a) are you trying to ssh from the server to the client or vice versa? b) did you create the rsa keys on the client or on the server?

All of the steps that you described seems to be OK, so it is definately something small that is hampering progress.

---

### Post by porchrat on 2008-10-22
I used a flash drive to copy it across.  Is that not allowed?  I really see no reason why it can't be done like that.

---

### Post by porchrat on 2008-10-22
> **mschutte said:**
> I just went back and re-read the entire post just to make sure we didn't miss something somewhere. I just have to clarify two things. a) are you trying to ssh from the server to the client or vice versa? b) did you create the rsa keys on the client or on the server?

All of the steps that you described seems to be OK, so it is definately something small that is hampering progress.

Trying to connect from client to server and created the keys on client machine

---

### Post by mschutte on 2008-10-22
Yes it could be the source of your frustration. Were you able to ssh between the server and the client before you created the rsa keys?

> **porchrat said:**
> I used a flash drive to copy it across.  Is that not allowed?  I really see no reason why it can't be done like that.

---

### Post by No-Neck on 2008-10-22
May I suggest you start again with the key making process. Create the key on the server, do the 'cat' part, etc. And copy the key to the client. It shouldn't take long.

---

### Post by porchrat on 2008-10-22
> **mschutte said:**
> Yes it could be the source of your frustration. Were you able to ssh between the server and the client before you created the rsa keys?

Yes indeed I was...however using password authentication is not secure enough for what I need.

I tried using this command:

```
scp /home/client_system_username/.ssh/id_rsa.pub server_username@server_IP
```

obviously with all the proper bits in it.  It didn't return any errors, but I never received the file in my home directory...any ideas?

---

### Post by mschutte on 2008-10-22
Agree here with No-Neck. It would the easiest to create the keys on the client and to use ssh-copy-id to take them to the server. I would not recoomend the use of the flash drive.

---

### Post by porchrat on 2008-10-22
> **No-Neck said:**
> May I suggest you start again with the key making process. Create the key on the server, do the 'cat' part, etc. And copy the key to the client. It shouldn't take long.

tried generating new keys...got the same problem.  I think that mschutte may be right...perhaps the answer is to make them password authenticate again so that they can ssh...use scp (or mschutte's command) to copy the rsa_id.pub across and then do the "cat" and reactivate rsa authentication and restart the sshd?

---

### Post by porchrat on 2008-10-22
what does this line from the sshd_config file mean?

```
PubkeyAuthentication no
```

I had it set to "yes" and got the error I've mentioned before, but when I set it to "no" I merely get this return from the client when I attempt an ssh:

```
Permission denied ().
```

???

---

### Post by mschutte on 2008-10-22
If you use the the -i option with ssh-copy-id command you do not have to do the cat file to authorized_keys bit. It is done automatically. The command will look something like this: 
*ssh-copy-id -i /home/username/.ssh/id_rsa.pub username@hostname*




> **porchrat said:**
> tried generating new keys...got the same problem.  I think that mschutte may be right...perhaps the answer is to make them password authenticate again so that they can ssh...use scp (or mschutte's command) to copy the rsa_id.pub across and then do the "cat" and reactivate rsa authentication and restart the sshd?

---

### Post by No-Neck on 2008-10-22
I would imagine that is to allow you to log in with the public key (id_rsa.pub). Which is why is just denied you after you disabled it, no permitted login methods?

---

### Post by porchrat on 2008-10-22
OK basically here is my progress so far.

I finally managed to run mschutte's command and it did indeed place a preconfigured file in the correct location /home/username/.ssh/authorized_keys (even had the right permissions)

Problem is that still didn't resolve the issue.  I can ssh just fine using passwords, but I can't ssh with RSA keys...maybe I'll try DSA keys in the morning, but I doubt it will make a difference.  For now I am exhausted and in need of some rest, please don't let that stop you giving me advice on this though as I will look at it in the morning.

Grr this is frustrating.

Anyone have any idea what is wrong with this setup?

---

### Post by mschutte on 2008-10-22
There is one other option you can try. It is to use the ssh-agent and ssh-add commands to add your private key to the agent when using the ssh service.

Let me quickly give you the commands then you can try them in the morning and see if it helps:

First you have to execute ***ssh-agent bash***, that is if you are running the bash shell which is the default anyway.

Second you execute ***ssh-add /home/username/.ssh/id_rsa*** Please ensure that you do this from the client machine where you created the rsa keys and substitute the correct username.

Lastly you ssh to the server and bash, being the agent, will automatically use the id_rsa key (private key) to respond to the ssh challenge from the server. No passwords needed. Until the next reboot that is...

---

### Post by porchrat on 2008-10-23
> **mschutte said:**
> There is one other option you can try. It is to use the ssh-agent and ssh-add commands to add your private key to the agent when using the ssh service.

Let me quickly give you the commands then you can try them in the morning and see if it helps:

First you have to execute ***ssh-agent bash***, that is if you are running the bash shell which is the default anyway.

Second you execute ***ssh-add /home/username/.ssh/id_rsa*** Please ensure that you do this from the client machine where you created the rsa keys and substitute the correct username.

Lastly you ssh to the server and bash, being the agent, will automatically use the id_rsa key (private key) to respond to the ssh challenge from the server. No passwords needed. Until the next reboot that is...

When I try to add the key it says:
Could not open a connection to your authentication agent.

Perhaps that means the key isn't signed, and needs to be?  Perhaps that is the problem?  I will investigate further, but please once again feel free to post advice, comments and help.

EDIT: Looks like I sorted it out, turns out you need to run those commands as root (duh...silly me)...will try this out now

---

### Post by porchrat on 2008-10-23
OK gave it a go and I get this:

```
Failed to add the host to the list of known hosts (/home/user/.ssh/knwon_hosts)
Permission denied (publickey)

```

EDIT: OK it doesn't add it to known_hosts because my user doesn't have execute permissions for the /home/user/.ssh directory (chmod 600 not chmod 700) so that is that mystery solved, but it still shouldn't make a difference as I've now run the thing with sudo and it added it no problem.

Thing is when I set 

```
RSAAuthentication yes
PubkeyAuthentication yes
PasswordAuthentication yes 
```

then it logs in just fine, does this mean that it only needs one method of authentication in order to establish a connection, and hence password authentication negates the need for the key?  Or that for some reason my server doesn't want to accept RSA keys without a password?

Also please note that when I attempt to ssh from the client I am not prompted for my RSA key passphrase, which seems odd as I have read that it should prompt me.  Perhaps the client can't read my id_rsa file?

---

### Post by porchrat on 2008-10-23
Hi all I finally managed to solve it!

I set "LogLevel DEBUG3" to get a more verbose log.  Turns out that even though I had set the server to get the authorized_keys from a certain location I had chosen, it was still defaulting to the /home/ssh_login_username/.ssh/ directory.  I merely moved the authorized_keys file in their, changed the ownership and that solved it.

Thanks all for your help I have actually gained a lot of knowledge form this experience which I suppose is part of the process.

---

