---
title: "receiving GPG encrypted e-mail in evolution"
date: 2008-07-28
forum: General Help
---

### Post by sfabel on 2008-07-28
Hi,

I am using the latest Evolution distributed with Ubuntu 8.04.1, and have the following problem: whenever someone sends me an encrypted e-mail (he is using Thunderbird+Enigmail), the message is empty, but has an attachment. This attachment contains the clear-text of the message, however it is not displayed.

I suppose the workaround/solution would be to get Evolution to just interpret the "attachment.dat" as plain text and display it, but how do I get Evolution to do so?

Thanks,
Stephan

---

### Post by Norman Grahams on 2008-07-31
I find clicking on the button to tell evolution to display the attachment inline works. It then prompts for the password again if you haven't asked it to remember it, but does display the message.

This is testing with messages sent to me encrypted using Thunderbird. The problem I then have is that Evolution won't recognise that they're signed, and likewise visa versa.

---

### Post by grigio on 2008-08-03
Save attachment.dat and read it :)

The bug is [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/184839](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/184839)

---

