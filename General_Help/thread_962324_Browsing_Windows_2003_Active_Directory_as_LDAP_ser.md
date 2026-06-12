---
title: "Browsing Windows 2003 Active Directory as LDAP server with Evolution"
date: 2008-10-29
forum: General Help
---

### Post by lviggiani on 2008-10-29
Hi,
I'm trying to connect to a Windows 2003 Active Directory as a LDAP server from my address book in Evolution.
It doesn't work... I don't know where I'm doing wrong. It could be either Evolution settings or Active Directory setting (or even both) :(.

This are the settings:

**Active Directory:**
- domain name: e-levelcom.local
- added a new *Organization Unit* called *Contacts*
- added contacts to OU *Contacts*
- in *Windows Firewall* open ports 389 and 3268

**Evolution:**
- Server: *my server IP*
- Port: 389 (no encryption) (also tested 3268 )
- Login Method: DN
- Login: *DOMAIN\user*
- Search Base: DC=e-levelcom,DC=local,OU=Contacts (*Find Possible Search Bases* button works)
- Search Scope: Sub
- all the rest is default

What happens:
Selecting my LDAP Server from Evolution it asks for my domain password (ok).
Then it shows...

[I]There are no items in this view
Double-click to create a new Contact[/I]

...whereas contacts should be shown

If I double click, the "new contact" form appears but all fields are disabled.

Can anyone help me please?
Thanks in advance!

---

### Post by a_hanley on 2009-04-16
Hi lviggiani,

I understand how frustrating this is .. Evolution will not display the AD contacts however if you search via the search tab it should display the results.

You might also want to try setting the search base to CN=users,DC=e-levelcom,DC=local

Everything else that you set looks correct.

Hope this helps.

Alan

---

### Post by stelmobarbosa on 2010-09-03
Try to leave the DETAILS/SEARCH FILTER in Blank. And check the box in DETAILS tab "Travel this book until the end", i&#7743; not shure if the sentence in english is exactly this, but it's the last chekbox in DETAILS TAB

---

### Post by stelmobarbosa on 2010-09-03
My configuration for LDAP server in CONTACTS is correct the problem i have is that i just get de users from the OU i used in the Search Base. If i have OU=general, DC=mycompany,DC=local then i cant see other users inside OU within the General OU.

---

