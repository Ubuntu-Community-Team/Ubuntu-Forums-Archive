---
title: "small online problem with Windows after installing Ubuntu"
date: 2008-08-24
forum: General Help
---

### Post by scalywag66 on 2008-08-24
I read the threads I thought would be relative to my situation, so if my question has been answered already, my apologies.

Well, I downloaded and installed Ubuntu OS on my machine, just to try it out. It seems like a cool and easy operating to navigate through, and so far I like what I see and am able to do it with it.

Problem is, while Ubuntu is able to go online, Windows is incapable of it now. Going into the CMD prompt and doing IPCONFIG brings up "Unable to Query Host Name". My friend and I had this problem and I was able to fix it by uninstalling the Ethernet NIC adapter and letting Windows reinstall upon reboot. This time however, that solution seems to be a futile attempt, and right now I'm on Ubuntu trying to sort this out.

What happened to Windows online capability when I installed Ubuntu, and how can I get Windows to work online again?

Sorry if similiar problem has already been addressed and thanks!!!

---

### Post by coffeecat on 2008-08-24
It would be helpful if you post more details of your Windows and Ubuntu installations. I can't offhand think of a likely scenario where Ubuntu would interfere with Windows connecting to the network, and this sounds like a Windows problem. However:

Do you have Ubuntu and Windows on separate machines?

Or are you dual-booting Windows and Ubuntu on the same machine?

Or have you installed Ubuntu with Wubi inside your Windows partition?

Also, some details of your network/type of router might be useful.

---

### Post by scalywag66 on 2008-08-24
Well lets see, after installing Ubuntu, it told me I had to reboot, but I chose to reboot later cause I wanted some last details before I rebooted.  I surfed around the net on Windows for about another minute or two before rebooting and checking out Ubuntu, just to make sure I wasn't missing any details.  

I reboot, let Ubuntu finish what it had to do, explored it for like 10 minutes, then went back to Windows, and VOILA!, no internet.   So I do the ipconfig command in CMD and got the error I had gotten before, tried the same method I did to fix it, but nothing.

I boot up the PC and have my choice between Ubuntu or Windows.

I've tried Winsock TCP/IP Repair Tool and some various manual methods to correct the issue.  At worst, the most I may have to do is uninstall Ubuntu and try the original method again.

---

### Post by scalywag66 on 2008-08-24
Well, I had it going, but then it lost its ip again :(

---

### Post by scalywag66 on 2008-08-30
Solution remembered and am back online on Windows!!!  What a newb I am.  I can't believe I forgot about the other step to fixing the issue.


All you have to do for if the machine can't grab an i.p. is...

1. **search for the file 'tcpip.sys'**
    - results will show 5 or so files named 'tcpip'
    - 2 of the results(both will be named 'tcpip.sys') will be from a recent modified date while the other 3(named 'tcpip.sys.original') will be from a much earlier date

2. **delete the two recent 'tcpip.sys' files **

3. **rename the 'tcpip.sys.original' files to 'tcpip.sys'**

4. **uninstall the NIC Ethernet adapter**
    - Start > right click My Computer > properties > click Hardware tab > Device Manager > Network Adapters > right click NIC Ethernet Adapter and uninstall

5. **reboot**
    - when Windows restarts, it'll detect NIC Adapter as 'New Hardware found' and will install

6. **go online!!!**

---

