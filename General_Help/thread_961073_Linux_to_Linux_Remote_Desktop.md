---
title: "Linux to Linux Remote Desktop"
date: 2008-10-28
forum: General Help
---

### Post by raiderleaf on 2008-10-28
Hello, I'm trying to use a remote desktop from my Ubuntu 8.04 to a Fedore Core System, which should be of one of the newest versions for what its worth. Anyways, the address of the server I'm trying to contact is wopr.csl.mtu.edu , and I want to remote desktop to my user login there. What applications will I need in order to do this?

Thank you,

raiderleaf

---

### Post by alienprdkt on 2008-10-28
NoMachine

[http://ubuntuforums.org/showthread.php?t=202394](http://ubuntuforums.org/showthread.php?t=202394)

[http://www.nomachine.com/installation.php](http://www.nomachine.com/installation.php)

---

### Post by raiderleaf on 2008-10-28
> **alienprdkt said:**
> NoMachine

[http://ubuntuforums.org/showthread.php?t=202394](http://ubuntuforums.org/showthread.php?t=202394)

[http://www.nomachine.com/installation.php](http://www.nomachine.com/installation.php)

I tried installing it and connecting, and it looked all good until this image popped up, which I have attached.


What gives? -Raiderleaf

---

### Post by alienprdkt on 2008-10-28
1. Make sure openssh-server is installed on the server machine/s and that you can ssh into into those machines. See this link ([https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)). Just one caveat. You must ensure that password based authentication is enabled in the /etc/ssh/sshd_config file of the server machine. Initially you should also use the standard port 22 for ssh as well.

2. Download these files from here ([http://www.nomachine.com/download-package.php?Prod_Id=6](http://www.nomachine.com/download-package.php?Prod_Id=6))

nxclient_3.2.0-14_i386.deb
nxnode_3.2.0-13_i386.deb
nxserver_3.2.0-16_i386.deb

3. Put the files in the home directory of the machine you want to use as the server, open a terminal, and install them:

sudo dpkg -i *.deb

note: make sure that these are the only .deb packages in your home directory when you do this.

4. Repeat the above on the client machine - on the client you only need the nxclient package and not the nxserver and nxnode packages

5. At this stage it's worth testing that everything works 'as is'. You may have to do a 'killall gnome-panel' before the NX entry appears in the menu, but once it has you'll find it under applications/internet. Open the NX connection wizard and follow along. You should be able to log in as a normal user with the user name and password that you normally log into the system with. If all goes well a session should open on your desktop displaying the server machine's desktop.

6. If all went well you will now want to change the default ssh keys that the NX server uses. When you first install the nx packages they ship with default keys that are the same for everyone. Potentially this means that anyone with the nxclient package installed could authenticate against your server. Not good! However, changing these keys is simple. Just log into the server (or ssh to the server) and do the following:

sudo su
/usr/NX/scripts/setup/nxserver --keygen
chown nx:root /usr/NX/home/nx/.ssh/authorized_keys2
chmod 0644 /usr/NX/home/nx/.ssh/authorized_keys2
chown nx:root /usr/NX/home/nx/.ssh/default.id_dsa.pub
chmod 0644 /usr/NX/home/nx/.ssh/default.id_dsa.pub

Then copy the default.id_dsa.pub file to the client. I did this using scp from the client machine, e.g.

scp [email]user@server:/usr/NX/share/keys/default.id_dsa.key[/email] .

But you could just as easily copy it to a usb flash drive and transfer it to the client. Once you've saved it to the client machine's home directory you should rename the key from default (I use my user name) and copy it to the /usr/NX/share/keys/ directory:

sudo cp default.id_dsa.key /usr/NX/share/keys/user.id_dsa.key

Now test that you can connect to the nx user account on the server with this key:

ssh -i /usr/NX/share/keys/user.id_dsa.key nx@server

You shouldn't be prompted for a password. If you can connect as the nx user just type quit to exit. Then launch the nx client from the menu, hit configure, and then the key button on the general tab. Delete the exiting key and press the import button. Import the key that you've just saved in the /usr/NX/share/keys directory. Save everything and then try connecting with the client.

Optional steps

7. If all went well you can now change the default ssh port to a non-standard one (say 2222 for this example). Go back to the server machine (or shh to it) and edit three files to make the changes.

First edit the /usr/NX/etc/server.cfg file:

sudo gedit /usr/NX/etc/server.cfg

Look for these entries:

#SSHDPort = "22"
#SSHDAuthPort = "22"

Uncomment and change 22 to 2222. Save and close.

Then edit /usr/NX/etc/node.cfg:

sudo gedit /usr/NX/etc/node.cfg

Look for this entry:

#SSHDPort = "22"

And again uncomment and change the port number. Save and close.

Finally edit /etc/ssh/sshd_config

sudo gedit /etc/ssh/sshd_config

Look for this entry:

Port 22

And again change the port, save and close.

Finally, restart ssh:

sudo /etc/init.d/ssh restart

On the client machine you should then launch the nx client, press the configure button, and enter the new port in the general tab.

That's it. You should now be able to connect to the nxserver on a non-standard port with a custom ssh key.

8. For added security you might also want to go back to the server machine and edit the /usr/NX/etc/server.cfg file again. Find this line:

#EnableUnencryptedSession = "1"

Uncomment it and change the "1" to a "0"

This will force nx to use ssl encryption at all times.

That's basically it. The only problem I have with nx so far is not being able to disable password based authentication in my sshd_config. There is a work around which involves adding system users to the nx server and then using the nx database rather than ssh to authenticate. However, I haven't tried this, so I'm not able to comment on how well it works, What I've done instead is limit the number of users who can ssh into the server machine (nx must be a listed user), and restricted access in my firewall to only allow certain machines through.

---

### Post by raiderleaf on 2008-11-09
> **alienprdkt said:**
> 1. Make sure openssh-server is installed on the server machine/s and that you can ssh into into those machines. See this link ([https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)). Just one caveat. You must ensure that password based authentication is enabled in the /etc/ssh/sshd_config file of the server machine. Initially you should also use the standard port 22 for ssh as well.

2. Download these files from here ([http://www.nomachine.com/download-package.php?Prod_Id=6](http://www.nomachine.com/download-package.php?Prod_Id=6))

nxclient_3.2.0-14_i386.deb
nxnode_3.2.0-13_i386.deb
nxserver_3.2.0-16_i386.deb

3. Put the files in the home directory of the machine you want to use as the server, open a terminal, and install them:

sudo dpkg -i *.deb

note: make sure that these are the only .deb packages in your home directory when you do this.

4. Repeat the above on the client machine - on the client you only need the nxclient package and not the nxserver and nxnode packages

5. At this stage it's worth testing that everything works 'as is'. You may have to do a 'killall gnome-panel' before the NX entry appears in the menu, but once it has you'll find it under applications/internet. Open the NX connection wizard and follow along. You should be able to log in as a normal user with the user name and password that you normally log into the system with. If all goes well a session should open on your desktop displaying the server machine's desktop.

6. If all went well you will now want to change the default ssh keys that the NX server uses. When you first install the nx packages they ship with default keys that are the same for everyone. Potentially this means that anyone with the nxclient package installed could authenticate against your server. Not good! However, changing these keys is simple. Just log into the server (or ssh to the server) and do the following:

sudo su
/usr/NX/scripts/setup/nxserver --keygen
chown nx:root /usr/NX/home/nx/.ssh/authorized_keys2
chmod 0644 /usr/NX/home/nx/.ssh/authorized_keys2
chown nx:root /usr/NX/home/nx/.ssh/default.id_dsa.pub
chmod 0644 /usr/NX/home/nx/.ssh/default.id_dsa.pub

Then copy the default.id_dsa.pub file to the client. I did this using scp from the client machine, e.g.

scp [email]user@server:/usr/NX/share/keys/default.id_dsa.key[/email] .

But you could just as easily copy it to a usb flash drive and transfer it to the client. Once you've saved it to the client machine's home directory you should rename the key from default (I use my user name) and copy it to the /usr/NX/share/keys/ directory:

sudo cp default.id_dsa.key /usr/NX/share/keys/user.id_dsa.key

Now test that you can connect to the nx user account on the server with this key:

ssh -i /usr/NX/share/keys/user.id_dsa.key nx@server

You shouldn't be prompted for a password. If you can connect as the nx user just type quit to exit. Then launch the nx client from the menu, hit configure, and then the key button on the general tab. Delete the exiting key and press the import button. Import the key that you've just saved in the /usr/NX/share/keys directory. Save everything and then try connecting with the client.

Optional steps

7. If all went well you can now change the default ssh port to a non-standard one (say 2222 for this example). Go back to the server machine (or shh to it) and edit three files to make the changes.

First edit the /usr/NX/etc/server.cfg file:

sudo gedit /usr/NX/etc/server.cfg

Look for these entries:

#SSHDPort = "22"
#SSHDAuthPort = "22"

Uncomment and change 22 to 2222. Save and close.

Then edit /usr/NX/etc/node.cfg:

sudo gedit /usr/NX/etc/node.cfg

Look for this entry:

#SSHDPort = "22"

And again uncomment and change the port number. Save and close.

Finally edit /etc/ssh/sshd_config

sudo gedit /etc/ssh/sshd_config

Look for this entry:

Port 22

And again change the port, save and close.

Finally, restart ssh:

sudo /etc/init.d/ssh restart

On the client machine you should then launch the nx client, press the configure button, and enter the new port in the general tab.

That's it. You should now be able to connect to the nxserver on a non-standard port with a custom ssh key.

8. For added security you might also want to go back to the server machine and edit the /usr/NX/etc/server.cfg file again. Find this line:

#EnableUnencryptedSession = "1"

Uncomment it and change the "1" to a "0"

This will force nx to use ssl encryption at all times.

That's basically it. The only problem I have with nx so far is not being able to disable password based authentication in my sshd_config. There is a work around which involves adding system users to the nx server and then using the nx database rather than ssh to authenticate. However, I haven't tried this, so I'm not able to comment on how well it works, What I've done instead is limit the number of users who can ssh into the server machine (nx must be a listed user), and restricted access in my firewall to only allow certain machines through.

Yikes that seems like a lot, but don't I have to have administrative privileges in order to install new software on the other computer anyways? I don't, which is a problem.

---

### Post by Mazin on 2008-11-09
what the crap is nomachine ???


You generally have two options for remote desktop, each of which accomplishes a different goal.

If you want to be able to control the active screen on the remote computer (i.e., see what the person sitting down at the computer sees, fight with him for mouse control, etc.), you can use VNC.  The remote computer needs to have a running VNC server, which is generally disabled for security.

In your case, however, it looks like you want to login to the computer and run commands on it that show up on your screen.  Since Unix has its roots in timesharing mainframes, this is trivial.

Run something like
```
ssh -XC yourname@wopr.csl.mtu.edu
```
and if you successfully login, you'll get a remote shell that you can run commands on the other computer with.  Try running `uname`.

Then, try running `xeyes` and see if graphical programs can appear on your end (enabled with the -X option for ssh).  This way, you can transparently use another computer's resources on your computer.

---

### Post by CLomax on 2008-11-10
VNC comes with Ubuntu, not sure about Fedora though.

---

### Post by raiderleaf on 2008-11-10
> **Mazin said:**
> what the crap is nomachine ???


You generally have two options for remote desktop, each of which accomplishes a different goal.

If you want to be able to control the active screen on the remote computer (i.e., see what the person sitting down at the computer sees, fight with him for mouse control, etc.), you can use VNC.  The remote computer needs to have a running VNC server, which is generally disabled for security.

In your case, however, it looks like you want to login to the computer and run commands on it that show up on your screen.  Since Unix has its roots in timesharing mainframes, this is trivial.

Run something like
```
ssh -XC yourname@wopr.csl.mtu.edu
```
and if you successfully login, you'll get a remote shell that you can run commands on the other computer with.  Try running `uname`.

Then, try running `xeyes` and see if graphical programs can appear on your end (enabled with the -X option for ssh).  This way, you can transparently use another computer's resources on your computer.

The ssh -XC method works great for starting applications on the other computer on my screen, thank you! I still am trying to find a way that I log in at the login screen remotely and see my desktop and everything on it. Is that possible? 

Thanks,

raiderleaf

---

