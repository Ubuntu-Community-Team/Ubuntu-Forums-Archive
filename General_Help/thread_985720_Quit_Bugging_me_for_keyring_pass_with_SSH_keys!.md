---
title: "Quit Bugging me for keyring pass with SSH keys!"
date: 2008-11-17
forum: General Help
---

### Post by paulisdead on 2008-11-17
Since upgrading to 8.10, whenever I first ssh to another box I have that I use an ssh key to login, I get prompted for my keyring password.  The point of setting up the key was so that I don't have to use a password to ssh to that box after I login.  So how do I get the keyring to stop pestering me over this?

---

### Post by psusi on 2008-11-17
Ummm... don't set a password on your private key?  Though that's not such a great idea since anyone who gets ahold of the private key file will be able to log in as you.

---

### Post by easoukenka on 2008-11-18
#!/bin/sh
if [ "$1" = "" ];  
then
	echo "syntax: ussh remote_username remote_server local_username local_server"
	exit 1
fi
ssh "$3"@"$4" "echo `ssh "$1"@"$2" cat .ssh/id_rsa.pub` >> .ssh/authorized_keys"


a little script I use to get in without passwords forever on that computer I am assuming you know how to generate the keys needed do them without passphrase or password

---

### Post by psusi on 2008-11-18
?

That script just fetches your public key from another computer and adds it to the keyring on this computer, so that in the future, that computer can ssh to this one using the key.

---

### Post by paulisdead on 2008-11-18
> **psusi said:**
> Ummm... don't set a password on your private key?  Though that's not such a great idea since anyone who gets ahold of the private key file will be able to log in as you.

I didn't set a password on the private key.  Let me explain this more clearly.  I open up a gnome terminal and I ssh to my file server.  Then in the GUI a seperate  window pops up asking for the gnome keyring password.  It won't prompt again until logout, but it's still annoying.

---

### Post by psusi on 2008-11-18
Ahhh, I bet it's ssh-agent.  The gnome keyring is probably acting as an ssh-agent and your server has ssh-agent support enabled as well, so when you login to the remote server, it tries to fetch your private key so you can use it to ssh from there to another machine if you want, without having to enter your password again, or even have your private key stored on the server.  Since the server asks for your machine to send the private key, gnome asks you for your keyring master password so it can find the key in your keyring.

---

### Post by paulisdead on 2008-11-19
> **psusi said:**
> Ahhh, I bet it's ssh-agent.  The gnome keyring is probably acting as an ssh-agent and your server has ssh-agent support enabled as well, so when you login to the remote server, it tries to fetch your private key so you can use it to ssh from there to another machine if you want, without having to enter your password again, or even have your private key stored on the server.  Since the server asks for your machine to send the private key, gnome asks you for your keyring master password so it can find the key in your keyring.

I guess I'm really not explaining this that well.  As soon as I type say "ssh hal" (my Debian server with no GUI) and hit enter, gnome keyring pops up asking for the keyring password on my ubuntu desktop.  This pops up before it allows me to connect to my file server, right after hitting enter in gnome terminal.  It's asking for the password for my local keyring.

---

### Post by psusi on 2008-11-19
Run set | grep SSH_AUTH_SOCK.  If that variable is set, then ssh is connecting to gnome-keyring and asking it to authenticate the session rather than reading the private key itself.  It is supposed to make it convenient by only requiring you to enter the keyring password once rather than every time you ssh, but since you aren't using a password at all...

---

### Post by paulisdead on 2008-11-20
> **psusi said:**
> Run set | grep SSH_AUTH_SOCK.  If that variable is set, then ssh is connecting to gnome-keyring and asking it to authenticate the session rather than reading the private key itself.  It is supposed to make it convenient by only requiring you to enter the keyring password once rather than every time you ssh, but since you aren't using a password at all...

Oh, no I am using a keyring password, I meant I hadn't set a password on the ssh key.

Thanks that gave me enough information to find what I needed on my own.  Here's the gconf command to turn off gnome keyring's ssh-agent that worked for me

gconftool-2 --set -t bool /apps/gnome-keyring/daemon-components/ssh false

---

