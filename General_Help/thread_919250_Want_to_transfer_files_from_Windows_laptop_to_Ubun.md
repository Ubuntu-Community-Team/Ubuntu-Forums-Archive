---
title: "Want to transfer files from Windows laptop to Ubuntu laptop."
date: 2008-09-13
forum: General Help
---

### Post by wretchedfellerbunchers on 2008-09-13
I'm really hoping I don't have to burn everything onto cds to transfer it over. I'm also having trouble installing programs. Any ideas?

---

### Post by kokkus on 2008-09-13
That programs thing should be posted in a new thread.
If you have internet connection on your Windows PC you can send them via FTP, Bluetooth, email or create a server.
Since your PCs are probably using the same internet connection you can simply setup a local FTP server in windows.

If you do not have internet connection you can also use your mobile's bluetooth, an iPod or stuff like that if you have.

I use an external hard driver for things like that, backups etc. I suggest you do the same fo the future.

Hope this helps you:)

---

### Post by mb_webguy on 2008-09-13
Are you saying that you have two laptops, one running Windows and one running Ubuntu?  If so, and if both computers are on a local network, you can transfer the files just as you would from one Windows machine to another, but you need to install some packages on the Ubuntu machine first.  

Right-click on a folder in Ubuntu and select "Sharing Options".  Check the box next to "Share this folder", then click "Create Share".  You will be prompted to install some packages.  Do so, then reboot your computer.  Now go to a folder you want to access from Windows and right-click it and select "Sharing Options" again.  Click the boxes next to "Share this folder", "Allow other people to write in this folder", and "Guest access (for people without a user account)".  Now click "Create Share".

Now you should be able to go to the Windows laptop and click on Network Neighborhood and locate the Ubuntu laptop.  You should see the folder you just set as a share on the Ubuntu laptop.  Just drag and drop the files from Windows to this share.

---

### Post by gali98 on 2008-09-13
If you go to Place -> Connect to server

then select windows share.
For server put in the ip of the computer or the name of the computer...

on the share put "c$" without the quotes.

leave folder empty
in the username, put the user on the windows laptop.
In the domain put the workgroup of the windows laptop (probably WORKGROUP or HOME unless you changed it)
then check add bookmark and type in a name for it and hit okay.
If it comes up then great! if not go to Computer then double click on the bookmark you created (on the left pane) and it should go there.

This will put you on the c drive of the computer.
Just navigate to where you want and copy and paste. If there is a large amount of files I suggest plugging both devices into your router, as it will go faster that way.

These computers must be on the same network to work. 
I use this all the time and it works great. 
Kory

---

