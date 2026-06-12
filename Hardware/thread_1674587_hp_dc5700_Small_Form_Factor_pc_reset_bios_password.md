---
title: "hp dc5700 Small Form Factor pc reset bios password"
date: 2011-01-24
forum: Hardware
---

### Post by COKEDUDE on 2011-01-24
Does anyone have any tools for hp dc5700 Small Form Factor pc reset bios password? I would like to reset the password without having to take the computer apart. I tried these tools. 

[http://www.cgsecurity.org/wiki/CmosPwd](http://www.cgsecurity.org/wiki/CmosPwd)
[http://rapidshare.com/#!download|80tl2|68277812|unlock6.zip|122](http://rapidshare.com/#!download|80tl2|68277812|unlock6.zip|122)

Here are the specs on the computer. 

[http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?lang=en&cc=us&prodClassId=-1&contentType=SupportManual&prodTypeId=12454&prodSeriesId=3249646](http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?lang=en&cc=us&prodClassId=-1&contentType=SupportManual&prodTypeId=12454&prodSeriesId=3249646)

---

### Post by hsoulen on 2011-01-24
> **COKEDUDE said:**
> Does anyone have any tools for hp dc5700 Small Form Factor pc reset bios password? I would like to reset the password without having to take the computer apart. I tried these tools. 

[http://www.cgsecurity.org/wiki/CmosPwd](http://www.cgsecurity.org/wiki/CmosPwd)
[http://rapidshare.com/#!download|80tl2|68277812|unlock6.zip|122](http://rapidshare.com/#!download|80tl2|68277812|unlock6.zip|122)

Here are the specs on the computer. 

[http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?lang=en&cc=us&prodClassId=-1&contentType=SupportManual&prodTypeId=12454&prodSeriesId=3249646](http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?lang=en&cc=us&prodClassId=-1&contentType=SupportManual&prodTypeId=12454&prodSeriesId=3249646)

Sorry my friend, I have tried a bunch of tools in the past and the most reliable method is "open the box and pull the CMOS battery".

That said, sometime re-flashing the BIOS with the same version will most times reset the password (that is if the flash utility will let you flash without the password) but this can of course be dangerous.

Sorry I don't have better advice.

Hank

---

### Post by COKEDUDE on 2011-01-24
> **hsoulen said:**
> Sorry my friend, I have tried a bunch of tools in the past and the most reliable method is **"open the box and pull the CMOS battery".**

That said, sometime re-flashing the BIOS with the same version will most times reset the password (that is if the flash utility will let you flash without the password) but this can of course be dangerous.

Sorry I don't have better advice.

Hank

I tried that. It didn't work. On this model you gotta play with the jumpers. My problem is I don't see the jumpers. 

These pictures have all given me an idea of what I am looking for. 

[http://bizsupport1.austin.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=120&prodSeriesId=4169539&prodTypeId=12454&objectID=c02579250](http://bizsupport1.austin.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=120&prodSeriesId=4169539&prodTypeId=12454&objectID=c02579250)
[http://www.google.com/imgres?imgurl=http://www.computerhope.com/issues/pictures/jumper.jpg&imgrefurl=http://www.shoponline2011.com/m~c-dog-supplies~b-31000300~f-663993-663992_651353-664003_651353-625402.aspx&usg=__bZO3-77SZt8RrPQ1JLo4t0c30WI=&h=160&w=200&sz=13&hl=en&start=175&zoom=1&tbnid=a9Pu6MGxPdZ4XM:&tbnh=126&tbnw=157&ei=8Mo9TeGMFYb4swO86dmkAw&prev=/images%3Fq%3Dhp%2Bcomputer%2Bjumpers%26um%3D1%26hl%3Den%26client%3Dfirefox%26rls%3D%257Bmoz:distributionID%257D:%257Bmoz:locale%257D:%257Bmoz:official%257D%26biw%3D1024%26bih%3D569%26tbs%3Disch:10%2C4995&um=1&itbs=1&iact=hc&vpx=641&vpy=350&dur=1189&hovh=128&hovw=160&tx=83&ty=152&oei=i8I9Tf3wNoiV8QPp9aSkCA&esq=2&page=12&ndsp=15&ved=1t:429,r:13,s:175&biw=1024&bih=569](http://www.google.com/imgres?imgurl=http://www.computerhope.com/issues/pictures/jumper.jpg&imgrefurl=http://www.shoponline2011.com/m~c-dog-supplies~b-31000300~f-663993-663992_651353-664003_651353-625402.aspx&usg=__bZO3-77SZt8RrPQ1JLo4t0c30WI=&h=160&w=200&sz=13&hl=en&start=175&zoom=1&tbnid=a9Pu6MGxPdZ4XM:&tbnh=126&tbnw=157&ei=8Mo9TeGMFYb4swO86dmkAw&prev=/images%3Fq%3Dhp%2Bcomputer%2Bjumpers%26um%3D1%26hl%3Den%26client%3Dfirefox%26rls%3D%257Bmoz:distributionID%257D:%257Bmoz:locale%257D:%257Bmoz:official%257D%26biw%3D1024%26bih%3D569%26tbs%3Disch:10%2C4995&um=1&itbs=1&iact=hc&vpx=641&vpy=350&dur=1189&hovh=128&hovw=160&tx=83&ty=152&oei=i8I9Tf3wNoiV8QPp9aSkCA&esq=2&page=12&ndsp=15&ved=1t:429,r:13,s:175&biw=1024&bih=569)
[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=120&prodSeriesId=1137830&prodTypeId=12454&objectID=c00503102](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=120&prodSeriesId=1137830&prodTypeId=12454&objectID=c00503102)
[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c02014355&lang=en&cc=us&taskId=115&contentType=SupportFAQ&prodSeriesId=4269976&prodTypeId=12454](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c02014355&lang=en&cc=us&taskId=115&contentType=SupportFAQ&prodSeriesId=4269976&prodTypeId=12454)
[http://www.cnsunnyit.com/products/HP-dc5700-motherboard_1255.html](http://www.cnsunnyit.com/products/HP-dc5700-motherboard_1255.html)

The most useful picture was this one. This shows what I see the best. 

[IMG]http://i255.photobucket.com/albums/hh133/COKEDUDEUSF/hp_dc5700_motherboard_2__52474.png[/IMG]

This comes hp's website and very vaguely describes whats on the motherboard. 

[IMG]http://i255.photobucket.com/albums/hh133/COKEDUDEUSF/hi.png[/IMG]

Here is the manual that this comes from. 

[http://h20000.www2.hp.com/bizsupport/TechSupport/CoreRedirect.jsp?redirectReason=DocIndexPDF&prodSeriesId=3249646&targetPage=http%3A%2F%2Fbizsupport1.austin.hp.com%2Fbc%2Fdocs%2Fsupport%2FSupportManual%2Fc00794304%2Fc00794304.pdf](http://h20000.www2.hp.com/bizsupport/TechSupport/CoreRedirect.jsp?redirectReason=DocIndexPDF&prodSeriesId=3249646&targetPage=http%3A%2F%2Fbizsupport1.austin.hp.com%2Fbc%2Fdocs%2Fsupport%2FSupportManual%2Fc00794304%2Fc00794304.pdf)

My problem is don't see where the Jumpers are. The part that I put a line next to says just **password** in the manual. When I look at the real motherboard picture and my motherboard I don't see the jumpers at all.

---

### Post by cascade9 on 2011-01-25
Clear CMOS is listed in that manual- SW50, between the PCI slots. 

Its an actual switch rather than a jumper. You just push the switch in for 10+ seconds.

---

### Post by hsoulen on 2011-01-25
> **cascade9 said:**
> Clear CMOS is listed in that manual- SW50, between the PCI slots. 

Its an actual switch rather than a jumper. You just push the switch in for 10+ seconds.

Well done!

Only one quick thing, the picture and the diagram don't "quite" match.

The photo shows the button at the end of the PCI slot, not between. If you have a card in the slot you will need to remove it first.

[IMG]http://i1136.photobucket.com/albums/n483/hsoulen/Mobo.jpg[/IMG]

Hank

---

### Post by cascade9 on 2011-01-25
> **hsoulen said:**
> Well done!

Only one quick thing, the picture and the diagram don't "quite" match.

The photo shows the button at the end of the PCI slot, not between. If you have a card in the slot you will need to remove it first.


Nope, thats a mounting hole you've pointed out there. The clear CMOS button is between the PCI slots (its the yellow circle)

---

### Post by xesexevol on 2011-01-25
I came across an article '[**Reset HP / Dell BIOS Password**]("http://findpassword.net/reset-hp-dell-bios-password/")' , it may help you.

---

### Post by hsoulen on 2011-01-25
> **cascade9 said:**
> Nope, thats a mounting hole you've pointed out there. The clear CMOS button is between the PCI slots (its the yellow circle)

ROFL! Indeed! Thanks for pointing that out, nice goof on my part.

What confused me was the picture is cut off at the bottom so the second PCI slot is almost not visible, took me a second to realize the damn PCI-E slot is white as well (should have looked at the retention clip)...

Yes, indeed the small yellow thing with the black button is the one.

Cheers!

Hank

---

### Post by COKEDUDE on 2011-01-25
> **cascade9 said:**
> Clear CMOS is listed in that manual- SW50, between the PCI slots. 

Its an actual switch rather than a jumper. You just push the switch in for 10+ seconds.

That just clears the cmos. On this model you gotta play with the jumpers. I already tried that cause it was easier to find than the jumpers. 

From the manufacturer of the motherboard. 

> Resetting the Password Jumper
To disable the power-on or setup password features, or to clear the power-on or setup passwords,
complete the following steps:
1. Shut down the operating system properly, then turn off the computer and any external devices,
  and disconnect the power cord from the power outlet.
2. With the power cord disconnected, press the power button again to drain the system of any residual
  power.
WARNING! To reduce the risk of personal injury from electrical shock and/or hot surfaces,
be sure to disconnect the power cord from the wall outlet, and allow the internal system
components to cool before touching.
CAUTION: When the computer is plugged in, the power supply always has voltage applied
to the system board even when the unit is turned off. Failure to disconnect the power cord
can result in damage to the system.
Static electricity can damage the electronic components of the computer or optional
equipment. Before beginning these procedures, ensure that you are discharged of static
electricity by briefly touching a grounded metal object. See the Hardware Reference
Guide on the Documentation and Diagnostics CD for more information.
3. Remove the computer cover or access panel.
4. Locate the header and jumper.
NOTE: The password jumper is green so that it can be easily identified. For assistance
locating the password jumper and other system board components, see the Illustrated Parts
Map (IPM) for that particular system. The IPM can be downloaded from [http://www.hp.com/](http://www.hp.com/)
support.
5. 6. Replace the computer cover or access panel.
7. Reconnect the external equipment.
8. Plug in the computer and turn on power. Allow the operating system to start. This clears the current
  passwords and disables the password features.
9. 
60
Remove the jumper from pins 1 and 2. Place the jumper on either pin 1 or 2, but not both, so that
it does not get lost.
To establish new passwords, repeat steps 1 through 4, replace the password jumper on pins 1 and
2, then repeat steps 6 through 8. Establish the new passwords in Computer Setup. Refer to the
Computer Setup (F10) Utility Guide on the Documentation and Diagnostics CD for Computer Setup
instructions.

---

