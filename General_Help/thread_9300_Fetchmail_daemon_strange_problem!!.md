---
title: "Fetchmail daemon strange problem!!"
date: 2004-12-27
forum: General Help
---

### Post by Alessio on 2004-12-27
Hi guys and ladies
If I try: fetchmail -v, it downloads any mail form my pop3 :)
if I try: fetchmail -d interval , it does'nt works when interval timeout! 
Top syas that fetchmail is execute, but nothing!
I insert "set daemon interval" in fetchmailrc, but it's the same!
It's strange !!

---

### Post by Alessio on 2004-12-27
[QUOTE=Alessio]Hi guys and ladies
If I try: fetchmail -v, it downloads any mail form my pop3 :)
if I try: fetchmail -d interval , it does'nt works when interval timeout! 
Top syas that fetchmail is execute, but nothing!
I insert "set daemon interval" in fetchmailrc, but it's the same!
It's strange !![/QUOTE]
 Up! Anyone knows????

---

### Post by randy on 2004-12-28
Whats the rest of your config file like?

---

### Post by whittycat on 2005-04-06
I have something similar. I have just installed Hoary (Kubuntu actually) and fetchmail says it fetches mail but the mail doesn't seem to reside anywhere. Not in ~/Mail, not in /var/spool/mail/<user> nowhere. I added a .procmailrc but no change. Is there something I have to to do to postfix to get it to deliver mail? Here is my .fetchmailrc

poll tuschin.blackcatnetworks.co.uk
proto IMAP
timeout 60
user solon
password <never mind>
folder INBOX.pat
keep
fetchall

Can you help?
Tony Sumner

---

### Post by whittycat on 2005-04-06
I still don't know what the cause of that was but I decided to re-install and fetchmail now works as it should. 

Tony Sumner

---

