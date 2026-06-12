---
title: "uw-imapd and SSL - how?"
date: 2005-11-29
forum: General Help
---

### Post by pestie on 2005-11-29
I just loaded my web/mail server with Ubuntu, and for the most part it's great. However (ever notice how there's always a "however"?), I can't for the life of me get uw-imapd to work with SSL. If I use something like netcat to talk directly to port 993, I can see quite plainly that it's *not* talking SSL at all - it just answers in plaintext.

I just want a secure IMAP server. Thunderbird doesn't support STARTTLS, so that's out. I don't want to use Maildir, so Cyrus IMAPD is out. That leaves uw-imapd and *maybe* dovecot, but I know nothing about dovecot. If there's a way to make uw-imapd work, I'd love to hear about it. If dovecot will work, I'll use that. I'm getting a little desperate here, 'cause reading my mail spool with "less" kinda sucks. :smile:

Thanks in advance for any and all replies.

---

### Post by pestie on 2005-11-29
Bump!

---

### Post by jliedeka on 2005-11-29
I set up Courier IMAP and set it to only start imaps.  I haven't tried uw-imap.  Thunderbird plays well with Courier.  But you do need Maildirs for Courier.

---

