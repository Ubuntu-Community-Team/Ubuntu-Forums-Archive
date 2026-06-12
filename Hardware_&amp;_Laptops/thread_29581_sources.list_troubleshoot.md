---
title: "sources.list troubleshoot"
date: 2005-04-24
forum: Hardware &amp; Laptops
---

### Post by young on 2005-04-24
Hi there,

    I just modified my sources.list file to get the update and nothing has been working out for me.  Here's what I have so far:


   .....
   #Uncomment the following two lines to fetch update software from the network
  
    deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
    deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe

  #Uncomment the following two lines to add software from the 'universe'   
  #repository
  #N.B. software from this repository is not supported by the Ubuntu team..etc   
  #etc

  deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
  deb-src [http://archive.ubuntu.com/](http://archive.ubuntu.com/) ubuntu/ warty universe

  deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
  deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

  deb http:// archive.ubuntu.com/ubuntu/ warty multiverse
  deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

  deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
  deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
  deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
//------------------------------------------------------------------------------------------------------

and I get these whole bunch of error messages.  What am I doing wrong? Does anyone know? (if your sources.list file works, would you mind hooking me up with the file (how about helping a newbie out in his difficult time? hehe)  Anyhow,  thank you in advance, and any ideas would be much appreciated.


                                                                                       Cheers,

                                                                                                                Young

---

### Post by gunnyman on 2005-04-24
what error messages are you getting?

---

### Post by young on 2005-04-25
Hello there,

    Thank you very much for your reply.  I have lines and lines of error messages  
  when I type in 'apt-get update', but here are the errors:

   Err [http://archive.ubuntu.com](http://archive.ubuntu.com)  warty/main Packages 
   Temporary failure resolving 'archive.ubuntu.com'
//-----------------------------------------------------------------------------------------------------

   Err cdrom://Ubuntu_4.10_Warty Warthog_-Preview i386 Binary-1 (20041020) unstable/main Packages

   Please use apt-cdrom to make this CD recognized by APT.  apt-get update cannot be used to add new CDs

//-----------------------------------------------------------------------------------------------------
 
   W:Couldn't stat source package list cdrom://Ubuntu-4.10_Warty Warthog- Preview i386 Binary-1 (20040120) unstable/restricted Packages

 //---------------------------------------------------------------------------------------------------

  Just out of curiousity, does my internet have to work in order for the whole
 'apt-get update' to work?  Also, what are in the update files?  Once again, thank you for your reply and I hope to hear from you soon.

---

### Post by az on 2005-04-25
[QUOTE=young]Hello there,

    Thank you very much for your reply.  I have lines and lines of error messages  
  when I type in 'apt-get update', but here are the errors:

   Err [http://archive.ubuntu.com](http://archive.ubuntu.com)  warty/main Packages 
   Temporary failure resolving 'archive.ubuntu.com'
//-----------------------------------------------------------------------------------------------------

   Err cdrom://Ubuntu_4.10_Warty Warthog_-Preview i386 Binary-1 (20041020) unstable/main Packages

   Please use apt-cdrom to make this CD recognized by APT.  apt-get update cannot be used to add new CDs

//-----------------------------------------------------------------------------------------------------
 
   W:Couldn't stat source package list cdrom://Ubuntu-4.10_Warty Warthog- Preview i386 Binary-1 (20040120) unstable/restricted Packages

 //---------------------------------------------------------------------------------------------------

  Just out of curiousity, does my internet have to work in order for the whole
 'apt-get update' to work?  Also, what are in the update files?  Once again, thank you for your reply and I hope to hear from you soon.[/QUOTE]

Yes, you must be on the net for your computer to see if there are new packages.

The people who wite the applications release the code.  The package maintainers take the code and make adjustments so that it fits into the Ubuntu system.  They upload the source packages to the archive and they get built into binary packages.  To run a program, all you need in the binary.

When a bug is found in a package, the code gets changed and the modified package gets put into the updates archive.  When you do an update, you look to see if there are any packages that have been added to the archive.  

The only way to talk to another computer (the archive) is to be on the net.


One way to restore your sources.list file is to do 
sudo apt-setup
and add repositories as you are prompted.

---

### Post by young on 2005-04-25
Hello,

      Thank you very much for your reply.  I didn't even have a clue how the whole
   thing works.  But now I get it.

      The problem I have is that my internet is not working for some strange reason.
   I am using a Acer TravelMate 290 with Intel Centrino (so it means that I am 
   using a wireless network).  In this machine, I am dual-booting between Ubuntu 
   Linux and Windows XP.  So when I need to use the internet, I always have to 
   switch to the Windows XP.  But I intend to change all that my trying to make
   internet to work on Ubuntu as well.

       The Ubuntu, doesn't seem to be able to pick up the IP address automatically,
   after I went through the networking procedure.  One thing I tried to do was
   to install a dhcp3-server by typing 'apt-get install dhcp3-server'.  I always get a 
   message 'couldn't find file - dhcp3-server'.  So, I really don't have a clue what to 
   do to fix my internet.  Is there any other way I could fix my wireless network?

        This is information that I get when I type in 'iwconfig'
//------------------------------------------------------------------------------------------------------
 lo     no wireless extensions

eth0  no wireless extensions

eth    unassociated    ESSID: "young"
         Mode: Managed Channel = 0     Access Poiont: 00:00:00:00:00:00
         Bit Rate: 0kb/s   Tx-Power = 20dBm
         RTS thr: off    Fragment thr: off
         Encryption ket: off
         Power Management: off

sit     no wireless extensions
//------------------------------------------------------------------------------------------------------

  If you have any suggestions or ideas towards this issue, I would be more than happy to check it out.  Thank you again for your tips though- it was another important lesson for the newbie.

                                                                                      Cheers,

                                                                                            Young Chang  Song

---

### Post by az on 2005-04-25
Wireless is sometimes a problem.  You need to know what wireless card (or rather its' chipset) and get the driver.  I would suspect that you have a card that works in linux but cannot (yet) do WEP?  This is just a guess.

You may need to use ndiswrapper to utilize your card's windows driver.  You would need to prevent your current driver (module) from loading.  Find out what chipset you have and then do a search of the forums for that.  There should be plenty of threads here which deal with your wireless chipset.

If not, start another thread.

---

### Post by young on 2005-04-26
Hi there,

       Thank you so much for your advice.  Let me give this a shot and I will keep 
   you posted on what happens.


                                                                                                   Cheers,

                                                                                                                 Young

---

### Post by gerilaradio on 2005-05-04
i've got the problem with apt get sources.list before, but the problem not related with wireless card. my problem due to firewall and proxy, so can't get apt-get running well. the problem was settle now....

---

