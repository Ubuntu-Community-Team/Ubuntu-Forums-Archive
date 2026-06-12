---
title: "ATI Drivers - X1250 from ATI Tech Support"
date: 2010-01-26
forum: Hardware
---

### Post by Shibblet on 2010-01-26
This came directly from AMD/ATI Tech Support.
> AMD Service Notice:{ticketno:[8200275867]}&#8207;
From:	 [email]TECH.SUPPORT@AMD.COM[/email]
Sent:	Tue 1/26/10 12:10 PM
To:	shibblet
Dear Customer,

Your service request : SR #{ticketno:[8200275867]} has been reviewed and updated.

Response and Service Request History:

The X1250 chipset is 3 years old, it is also 4 generations old.  This is why it is considered legacy.  Why it is part of a current laptop release only the laptop manufacturer would be able to confirm.

There are currently no announced plans for driver development for any of the legacy chipsets in any operating system from AMD.

I have directed your feedback to the Linux Crew Team and Catalyst Crew Team, the driver developers.

In order to update this service request, please respond, leaving the service request reference intact.

Best regards,

AMD Global Customer Care

Original Email from me:
> Original Text
From:	shibblet
To:	[email]TECH.SUPPORT@AMD.COM[/email]
CC:	
Sent:	01/24/10 04:24:43
Subject:	Drivers for Linux

I just purchased an MSI Wind L2100 Notebook computer. This computer has an ATI x1250 Mobility Graphics Adapter built in. This computer is brand new, I have only owned it for just over 2 months.

I would like to run Ubuntu Linux on this computer, but there are no current video drivers. The current XServer in most new linux distributions is not compatible with the 9.3 or 9.4 Catalyst Drivers. As this is a new laptop, I can't imagine this driver being considered "legacy".

I have searched through many different Linux forums, including the Ubuntu forums, and I have come to the conclusion that this device is not supported for current versions of Linux. There are a lot of Ubuntu users out there, and plenty of people who use other forms of Linux, all of which would love to have driver support from ATI.

Is there something that can be done?

I propose we all write them emails and complain about the lack of support for ATI Drivers.

---

### Post by Yellow Pasque on 2010-01-26
fglrx is a dead-end. That's why they're working on a Gallium3D driver for R300-R500: [http://www.phoronix.com/scan.php?page=news_item&px=NzY4Ng](http://www.phoronix.com/scan.php?page=news_item&px=NzY4Ng)

---

### Post by jrusso2 on 2010-01-26
Talk to Handy he keeps saying open source support is right around the corner and will be better.

---

### Post by Shibblet on 2010-01-26
> **jrusso2 said:**
> Talk to Handy he keeps saying open source support is right around the corner and will be better.

Can you point me toward the thread?

---

### Post by ssri on 2010-01-27
> **jrusso2 said:**
> Talk to Handy he keeps saying open source support is right around the corner and will be better.

The only thing they will be better at is reaffirming the narrow worldview of FOSS zealots.  They will not have feature parity with their proprietary counterparts, especially when it comes to 3D.  How close or how far though remains to be seen.  That being said, I use the opensource drivers even if they are glitchy at times.  They are fine for my purpose, as I do not game or have a need to use any advance 3D capabilities.  The lack of dynamiclocks and the unease of configuring my S-Video output are vexing.  As a realist, I have to say that the opensource drivers are just okay; certainly they do not contain any of the puffy clouds and unicorns that some of its admirers see.

---

### Post by bluelamp999 on 2010-01-27
> **Shibblet said:**
> Can you point me toward the thread?

Here you go - [http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by bluelamp999 on 2010-01-27
> **ssri said:**
> The only thing they will be better at is reaffirming the narrow worldview of FOSS zealots. 

...

As a realist, I have to say that they are just okay; certainly they do not contain any puffy clouds and unicorns that some of its admirers see.

That's a bit harsh!:) For those of us excluded from the ATI support domain because of 'legacy' chipsets, the open source drivers offer a hope of decent 3D support...

---

### Post by Shibblet on 2010-01-27
Here's my response...

> From:	shibblet
To:	[email]tech.support@amd.com[/email]
CC:	
Sent:	01/26/10 14:17:24
Subject:	RE: AMD Service Notice:{ticketno:[8200275867]}


I do understand that this chipset is 3 years old and 4 generations old. But the current Catalyst drivers for Windows support the x1250, and Windows 7 has been available to the public for about 3 months. 

I understand that continuing support for an older product can be counter productive. But when a device falls into the non-supported category, couldn't a driver be released that the Linux community can use? As it is now, there is nothing that supports the x1250. I have to deal with a brand new computer, that has no functional Linux driver.

And they responded with...

> Dear Customer,

Your service request : SR #{ticketno:[8200275867]} has been reviewed and updated.

Response and Service Request History:

There are no official drivers from AMD for any mobility chipset in Windows 7.  Drivers for Windows 7 and mobility chipsets come from the laptop manufacturer not AMD.

The drivers from AMD for Windows 7 do not include support for the X1250 chipset, the lowest supported mobility chipset for the beta drivers from AMD was the HD2000 Series.  For the legacy desktop series cards the drivers customers are directed to for Windows 7 are the Vista legacy drivers.  There are no specific Windows 7 drivers.

I have directed the feedback to the Linux Crew Team on your behalf.

In order to update this service request, please respond, leaving the service request reference intact.

Best regards,

AMD Global Customer Care

And that's true.  It does use Vista Legacy Drivers.  But all of that can be damned!  I'm beginning to see why there are open source "Zealots" out there.  They know they can't depend on any of these corporations to EVER get them what they need.  So, keeping projects like this free is paramount.

It seems that I can only put faith in the Open Source Community to get functional ATI drivers for this computer.  How and where can I get the FOSS Drivers?

---

### Post by ssri on 2010-01-27
Well, if you installed Jaunty or Karmic, you should have them installed already.  If you want the latest of the latest, here are a few links:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1231030](http://ubuntuforums.org/showthread.php?t=1231030)
[http://ubuntuforums.org/showthread.php?t=1164013](http://ubuntuforums.org/showthread.php?t=1164013)
[http://ubuntuforums.org/showthread.php?t=1138645&highlight=ati](http://ubuntuforums.org/showthread.php?t=1138645&highlight=ati)

---

