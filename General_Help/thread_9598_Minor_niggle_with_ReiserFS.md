---
title: "Minor niggle with ReiserFS"
date: 2004-12-29
forum: General Help
---

### Post by logomancer on 2004-12-29
I've been having a minor problem with my ReiserFS partition. On boot up, I get the following message:

"Root filesystem appears to be mounted read-only. Skipping journal replay."

My question: How do I fix it so that reiserfs attempts to replay the journal when the filesystem is mounted read-write, later in the boot process?

---

### Post by jdong on 2005-01-06
It's not skipping replay later. It's just delaying it until the read-write remount, at which time syslog kicks in and prevents the replay message from making it to the console.

---

