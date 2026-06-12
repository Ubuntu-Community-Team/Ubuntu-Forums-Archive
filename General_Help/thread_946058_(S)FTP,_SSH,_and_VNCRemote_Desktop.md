---
title: "(S)FTP, SSH, and VNC/Remote Desktop"
date: 2008-10-12
forum: General Help
---

### Post by ju2wheels on 2008-10-12
Hi everyone, I am used to running my computer as a server and fully converted over to Ubuntu a few months ago. Since then however ive really been in the need for many of the services I ran on my Windows box but dont know how to properly configure these on Linux or what options are available.


1. (S)FTP:
   - Virtual Directories
   - Virtual Users (not sure if this is the proper term, essentially users that arent directly tied to the Linux system)
   - Groups (which I can use to set which virtual directories they can access and what permissions its users have)
   - Still support regular Linux accounts (I only want this for my admin account so I can access any directories I need to.

When initially looking this up I was leaning heavily towards vsftpd, but I couldnt find any documentation on how to set this up.

It is critical that I find documentation on how to configure all these services securely as I go to school on a campus where people tend to try to break into systems (even though they arent supposed to obviously). So I need to be able to also monitor its status all the time as simply as possible, and I know I can do this through the logs, but GUI notifiers would be a plus.


2. SSH

   - The main issue here is making sure I can configure it securely.
   - I also remember reading somewhere I could use it for tunneling ftp (aka sftp) but I didnt know how I would tie this with vfstp or other ftp daemons and also that it was possible to do VNC or remote desktop over SSH?

3. VNC/Remote Desktop

   - I would like to do this securely again, and as I stated above I heard it was possible to tunnel through or integrate with SSH but I have no idea how.
   - Are there any advantages of one method versus the other?

I would greatly appreciate any ideas, suggestions, and links to resources anyone may be able to provide.

Thanks

---

### Post by jamesrl on 2008-10-13
I don't use a ftp server (usually just scp or sftp) or vnc that much (though have had no real problems with vnc4server but I just launch it when I specifically want a vnc server and don't run it as a daemon).  
ssh is very easy to setup,
just 
```
sudo apt-get install openssh-server
```
[It's in your best interest not to use private RSA/DSA keys for passwordless logins, unless you have a strong passphrase on your private key.  But you don't really have to worry about that unless you plan on using ssh-keygen.]
Settings can be edited within /etc/ssh/sshd_config though you can probably keep default settings.  The biggest 'security' risk is whether you have weak login/password combinations (e.g., people can login via commonly guessed usernames like root, admin, user, ubuntu, games) or with passwords that are words from the dictionary (or only slight variations like E for 3), very short, etc.
Setting this up, also sets up sftp.

---

