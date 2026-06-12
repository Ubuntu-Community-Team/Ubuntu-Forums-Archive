---
title: "installing on PC (A) using PC (B)"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by mahela007 on 2009-01-29
is there any way to install ubuntu on computer(A) using computer (B) so that computer (A) will be able to run ubuntu even when it is disconnected from computer (B)

---

### Post by Pumalite on 2009-01-29
Network Install

For those people using a Windows machine as the source for a network install, it can be done. Hopefully below will help someone one day with this exact scenario.

1 - Use TFTP.exe to serve as a network boot DHCP (instructions at this post) - [http://hugi.to/blog/archive/2006/12/...ll-via-windows](http://hugi.to/blog/archive/2006/12/...ll-via-windows)

2 - Disable IIS (temporarily) - IIS has problems with some of the file name and file structures

3 - Extract the ISO to a folder on your harddrive (approx 7.5GB of space needed)

3 - Install Apache HTTP, edit the http.conf file change the "Document Root" (line 149) to the folder on your harddrive where you extracted Ubuntu and also change line 177 to the same directory. Do not use backslashes eg. c:\ubuntu must be in the http.conf file as c:/ubuntu

4 - Around line 203 of the http.conf file add "Allow from x.x.x.x" where XXX is the IP address of the computer you are installing from. OR (but be careful) you can say "Allow from all"

5 - Check that you can access this in your browser. (depends on how you config'd your apache)

5 - Then start TFTP.exe

6 - Set the remote machine to boot from network (check in your bios settings)

7 - It should boot from network and start installing.

A couple of posts that helped me out (which may help someone else in turn one day):
-----------------------------------------------------------------------------------
[https://help.ubuntu.com/community/In...sServerNetboot](https://help.ubuntu.com/community/In...sServerNetboot)
[http://hugi.to/blog/archive/2006/12/...ll-via-windows](http://hugi.to/blog/archive/2006/12/...ll-via-windows)
[http://ubuntuforums.org/showthread.php?t=332343](http://ubuntuforums.org/showthread.php?t=332343)
[https://help.ubuntu.com/community/In...on/FromWindows](https://help.ubuntu.com/community/In...on/FromWindows)

---

