---
title: "Java installation..."
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by CharlesWelsh on 2009-06-28
Okay... Day two of my Linux experience... And I have absolutely NO experience with a command prompt... If thats even what its called. I wanted to know if someone could help me out with this... I'm sorry if this is not the appropriate thread... All I ask for is limited criticism and possibly some help... Thank you -CJ

---

### Post by Boondoklife on 2009-06-28
Ok well I assume you are looking to install java? if this is so then look in the synaptic package manager.

Don't worry about the critics out there, many forget that they were noobs before too. Just don't forget to do a little leg work and search before asking things.

---

### Post by CharlesWelsh on 2009-06-28
okay lol i have done some research... and i am afraid to run the command thing. i look in the synaptic thing... and i get all of these java things... i wanted to know if i should install of them... or am i just like... doing the wrong things...

---

### Post by Boondoklife on 2009-06-28
That is the great thing about the manager is if you decide ya dont want it just uninstall it =P But if you are wanting the runtime then look for sun-java6-bin

---

### Post by eddier on 2009-06-28
iF you just want Java for running java apps etc then open up Synaptic (password) look for 'Sun Java6 JRE' select install,click on Apply at the top and  bobs your mothers uncle.

Open java is installed by default,but I found it didnt work nicely with JSymphonic or HJSplit. You can remove if desired.

To get applications to open with Java by default, right click on the relevant programs icon,select 'opens with' and then select java,apply and thats it. 

eddie):P

---

### Post by CharlesWelsh on 2009-06-28
Thank you. You know... lastnight I had my doubts about this OS (NO disrespect meant) And now... I am convinced that this is the best ive ever used... I used to be a OSX fan... but i love the simplisity of this one... Thank you very much

---

### Post by CharlesWelsh on 2009-06-28
Dammit... I just want to play runescape. And i cant get it to work. I installed it... and everything... but It stillsays i dont have it installed... Any tips.

---

### Post by Boondoklife on 2009-06-29
Haha yea runescape can be a %#$@% I had it working but had to do install java manually, not hard really!

1) download the jre6 r14 binary -> [http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)
2) then install the binary, open a terminal and do the following.
```

sudo su -
cp <insert the location of the downloaded file here> /usr/lib/jvm
cd cd /usr/lib/jvm/
bash <java bin file downloaded>

```

Once this is done you will need to create the link for the addon, are you running x86 or x64 version of ubuntu?

---

