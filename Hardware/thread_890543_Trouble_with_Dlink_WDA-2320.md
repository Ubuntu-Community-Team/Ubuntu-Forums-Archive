---
title: "Trouble with Dlink WDA-2320"
date: 2008-08-15
forum: Hardware
---

### Post by EscapeCharacter on 2008-08-15
Greetings All,

I bought a Dlink WDA-2320 card for my spare box running hardy-xubuntu and I can't seem to get it working. I have the restricted modules installed, lsmod lists ath_pci and the interface shows up in iw- and ifconfig. I can even go as far as doing a "iwlist ath0 scan" to see my wireless router as well as other networks in my area.

No matter what I try with this card however, it will not pick up an IP, not by using the networking daemons, nor by issuing commands to set the essid, ap MAC, encryption keys and using dhclient manually. I even gone so far as to turn encryption off completely to no avail. 

What is interesting is that the I cannot set the frequency or the channel on the card either (in fact, there is no channel listed in an "iwconfig ath0" output) and that the frequency listed continues to cycle upward. It is as if the card is stuck in scanning mode or something. Couple this with the fact that the power and enable lights on the back of the card keep flashing...not very reassuring.

Initially, I thought that the card I had was bad, but I returned it for a replacement and am having exactly the same trouble with the new card. I have searched the forums here as well as the net and I can't seem to find any info on this or anyone who has had the same problem (though there are many places where it is said that this card works OOTB, which is why I went with this card in the first place). I am beginning to fear that I might have some new hardware revision that is incompatible with the atheros driver.

I would appreciate any thoughts or suggestions at this point since I am truly at the end of my rope. Thanks in advance. -AB

---

