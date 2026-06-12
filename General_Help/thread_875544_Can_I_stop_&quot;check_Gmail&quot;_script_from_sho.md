---
title: "Can I stop &quot;check Gmail&quot; script from showing in terminal?"
date: 2008-07-30
forum: General Help
---

### Post by Browncoatdevil on 2008-07-30
I have a script that I'm using in conky to check my gmail. I also have terminal "embedded" in my desktop. Is there a way to keep terminal from showing the script every time gmail is checked?

Here's the script:

> import os
import string

#Enter your username and password below within double quotes
# eg. username="username" and password="password"
username="**********"
password="**********"

com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=string.find(msg,"<fullcount>")
index2=string.find(msg,"</fullcount>")
fc=int(msg[index+11:index2])

if fc==0:
   print "0 new"
else:
   print str(fc)+" new"

It's not a big deal, but I'd still like to change it.

Screenshot attached.

---

