---
title: "Beagle is not indexing my Evolution Exchange Emails."
date: 2008-11-04
forum: General Help
---

### Post by garymansell on 2008-11-04
Hi,

I cannot get beagle to index my emails which I access using Evolution's Exchange Connector.

I have installed the beagle-evolution-backend package as suggested in other posts.

Any ideas as it would be really helpful to be able to search my emails as well as my local files.

Thanks in advance for any help

Regards

Gary

---

### Post by maks_zbogar on 2008-12-03
I too have same problem. Just that I use pop email accounts.

I use Evolution 2.24.1 on Ubuntu 8.10 - Intrepid Ibex, with 8 pop accounts. 
First I wanted the Ubuntu's Tracker to index my Evolution emails and made anything possible to configure my Evolution email indexing, but result was allways 0/0 emails indexed.

After that I was told to install Beagle, so I did install "Beagle Search 0.3.8" and indexing of Evolution mail again returned 0/0 indexed emails. After that I was told again I have to install beagle-backend-evolution package. I did that too, but no result. 

Index information in Beagle is same as in Tracker: "EvolutionMail: 0". 
But I do have 80 emails in Evolution and I tried search after indexing was finished.

Is there any other option to search files and emails in same place on Ubuntu? 

p.s.: I have also attached print screen images of Beagle settings and index status.
Do you think there is something wrong with my Evolution database? Everytime I restart computer and open Evolution I need to enter my main account login password in order to access some "key library" or something like that. (sorry cant remember right now)

---

### Post by mirko_3 on 2008-12-29
Can't contribute, but I too can't get tracker or beagle to index evolution mails (nor nautilus metadata for that matter)... verry annoying

---

### Post by maks_zbogar on 2008-12-29
I received explanation that there is a problem because new Evolution use SQL format to store emails. All plugins / programs for tracker, beagle, mail notification..., were made for Evolution's old text format, so none of these plugins/programs can't read new Evolution emails anymore.

I guess all users of new Evolution will have to wait for new versions of tracker, beagle, mail-notification...

---

### Post by mirko_3 on 2008-12-29
I figured as much: [http://bugzilla.gnome.org/show_bug.cgi?id=557534](http://bugzilla.gnome.org/show_bug.cgi?id=557534)
It's been open for over two months though, doesn't seem to be getting much attention :(

---

### Post by casanostra on 2009-02-11
I have been able to force Beagle to index my (Exchange) mail by feeding it Evolution's mail directory explicitly. Some email search results show up as text files, which makes sense, and some actually shows under the "Conversations" category - including a separate category for attachments ("Documents"). In both cases, they open in the default text editor when double clicked.

While this solution is not perfect (at all), it does allow me to search and read my mail (raw source, though). Actually, that is arguably a step up from Evolution's own search, which causes the program to crash all too frequently.

I realize this only applies to the "old" text format. I'm running Evolution 2.24.3 with the OWA Exchange connector on Intrepid, and I have no idea why it's not using sqlite.

---

