---
title: "Testing OpenVPN"
date: 2008-10-07
forum: General Help
---

### Post by Thacchima on 2008-10-07
Dear all,

Have been trying to set up OpenVPN b/w two Win XP machines. Though the configuration seems to be successful as I was able to ping the server & the client, when capturing packets using WireShark, I observed that the transmitted packets are not sent thru UDP but thru SMB. 

The packet transfer is done by typing \\<vitrual IP> from Start -> Run and copying a file manually. Need to know is this the right way of testing OpenVPN? If not, request you to kindly let me know the right way of doing this pls.

Also, when examining the 'ping' requests using WireShark, the packets are sent again thru ICMP instead of UDP.

Am I going wrong somewhere?

Any suggestions on this is highly appreciated.

Thanx in advance...

---

### Post by Titan8990 on 2008-10-07
What types of results do you hope to get from this testing? Are you attempting to test the performance of openVPN?


> The packet transfer is done by typing \\<vitrual IP> from Start -> Run and copying a file manually. Need to know is this the right way of testing OpenVPN? If not, request you to kindly let me know the right way of doing this pls.

The \\ in Windows indicates SMB. I don't know what you are testing for so there is no way for me to say whether or not SMB is what you want to test...


> 
Also, when examining the 'ping' requests using WireShark, the packets are sent again thru ICMP instead of UDP.

This is what ICMP is for: [http://www.ietf.org/rfc/rfc0792.txt?number=0792](http://www.ietf.org/rfc/rfc0792.txt?number=0792)

---

### Post by Thacchima on 2008-10-10
First of all, thanx for your immediate response...

Actually, what I need is to see the transfered packets going encrypted thru UDP. Its now going in clear thru SMB when captured with WireShark. 

If possible, request you to kindly suggest me a mechanism to do this please.

---

### Post by Thacchima on 2008-10-10
Dear all,

I'm trying to configure OpenVPN b/w two Win XP machines & was quite successful. My configuration has a ethernet bridge connection as both the machines are in the same subnet.

I also have WireShark installed to check whether the packets really travel encrypted b/w these machines.

I'm now in a fix as how to send some packets b/w these two machines.

Therefore, it wud really of great help to me if any of u can let me know the method of sending the packets b/w two Win XP machines please. 

I also heard that we can't use the \\<machine IP> from Start -> Run as packets travels thru SMB instead of UDP with this option, it seems.

Any suggestions on this is highly appreciated.

Thanx & Regards...

---

### Post by Thacchima on 2008-10-14
It would be of great help if someone can help me to get through this...

I'm trying to test OpenVPN b/w two Win XP machines by downloading a file from server using FTP thru browser.

I'm trying to capture the packets by installing Wireshark in the client machine (though I'm not sure whether Wireshark can be present in the same m/c where the packets are flowing in !!!). 

When observed, it was found that these packets comes in via FTP & also in clear. Assuming that the packets between the machines should travel encrypted thru UDP, I'm not really sure whether this test approach is really a right step..

If not, request you to kindly suggest a mechanism to test OpenVPN (i.e.) how to see whether the packets really travel encrypted b/w the machines please...

Thanx in advance...

---

### Post by Thacchima on 2008-10-14
It would be of great help if someone can help me to get through this...

I'm trying to test OpenVPN b/w two Win XP machines by downloading a file from server using FTP thru browser.

I'm trying to capture the packets by installing Wireshark in the client machine (though I'm not sure whether Wireshark can be present in the same m/c where the packets are flowing in !!!). 

When observed, it was found that these packets comes in via FTP & also in clear. Assuming that the packets between the machines should travel encrypted thru UDP, I'm not really sure whether this test approach is really a right step..

If not, request you to kindly suggest a mechanism to test OpenVPN (i.e.) how to see whether the packets really travel encrypted b/w the machines please...

Thanx in advance...

---

### Post by overdrank on 2008-10-14
Thacchima Hi  and welcome please do not make multiple threads on the same issue. Threads merged. :)

---

### Post by Thacchima on 2008-10-14
I'm sorry for posting the same issue in different threads....

But still didn't get a solution for solving it :-(

---

### Post by overdrank on 2008-10-14
> **Thacchima said:**
> I'm sorry for posting the same issue in different threads....

But still didn't get a solution for solving it :-(

I understand if I could help I would. You may bump your thread one a day to bring it back to the attention to the forums while you search for you answer. Good luck :)

---

### Post by Thacchima on 2008-10-14
Thanx...

Hoping to get a suggestion soon :-)

---

