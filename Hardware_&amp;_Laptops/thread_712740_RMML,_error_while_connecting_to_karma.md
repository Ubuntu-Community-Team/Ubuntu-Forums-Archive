---
title: "RMML, error while connecting to karma"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by homerj742 on 2008-03-02
hey guys, I can't connect to my karma via RMML (first time trying this). 

here's the error:

> Failed to download the music database from the device. caused by:
Communication with the device failed or was rejected. caused by:
com.rio.protocol2.packet.StatusFailedException: You will not be able to connect to your device until you have properly configured it with a network password.
	at com.rio.protocol2.packet.AbstractStatusReplyPacket.checkStatus(AbstractStatusReplyPacket.java:53)
	at com.rio.protocol2.packet.AbstractStatusReplyPacket.read(AbstractStatusReplyPacket.java:60)
	at com.rio.protocol2.PearlRequest.readPacket(PearlRequest.java:156)
	at com.rio.protocol2.PearlRequest.readReply(PearlRequest.java:121)
	at com.rio.protocol2.PearlRequest.writePacketAndReadReply(PearlRequest.java:178)
	at com.rio.protocol2.PearlRequest.readLock(PearlRequest.java:385)
	at com.rio.protocol2.PearlProtocolClient.readLock(PearlProtocolClient.java:289)
	at org.jempeg.protocol.AbstractSynchronizeClient.download(AbstractSynchronizeClient.java:163)
	at org.jempeg.manager.SynchronizeUI.download(SynchronizeUI.java:177)
	at org.jempeg.manager.SynchronizeUI$2.run(SynchronizeUI.java:155)
	at java.lang.Thread.run(Thread.java:619)


any help would be greatly appreciated

---

