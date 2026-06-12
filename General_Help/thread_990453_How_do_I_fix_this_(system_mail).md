---
title: "How do I fix this? (system mail)"
date: 2008-11-22
forum: General Help
---

### Post by ardchoille42 on 2008-11-22
I have rkhunter installed and it writes to /var/spool/mail/mail but when I type "mail" into the terminal it says there is no mail for me. I know that /var/spool/mail/mail has content in it because the file isn't empty.

```

-rw------- 1 mail mail 745 2008-11-22 07:49 /var/spool/mail/mail

```

In a previous install of Ubuntu I was able to read mail simply by typing in "mail" in the terminal.

I was thinking I need to add myself to the mail group in order to read/write to /var/spool/mail/mail but System > Administration > Users and Groups has no mail group in it, though there is a mail group in /etc/group.

How do I fix this?
1) Add myself to the mail group? If so, how?
2) sudo chown me:mail /var/spool/mail/mail && sudo chmod 660 /var/spool/mail/mail ?
3) reconfigure mail to send to me (/var/spool/mail/me) instead of mail? If so, how?

---

### Post by Stebalien on 2008-11-22
Have you set up your smtp server correctly.  Rkhunter does not write directly to your mail spool file.  By default, exim4 is installed along with rkhunter.  You can check this by typing ```
aptitude show exim4
```
If you are using exim4, just do a quick google search for configuration instructions.  You can also use a different SMTP server altogether (i.e. postfix or sendmail).

---

### Post by ardchoille42 on 2008-11-22
> **Stebalien said:**
> Have you set up your smtp server correctly.  Rkhunter does not write directly to your mail spool file.  By default, exim4 is installed along with rkhunter.  You can check this by typing ```
aptitude show exim4
```
If you are using exim4, just do a quick google search for configuration instructions.  You can also use a different SMTP server altogether (i.e. postfix or sendmail).

I've never installed an SMTP server on this machine (had the machine for 3 years) and this problem didn't exist in the previous install of Ubuntu 8.10. In the previous install, there was no mail (username=mail) file in /var/spool/mail, but there was a me (my username) file in /var/spool/mail. exim4 is installed though.

---

