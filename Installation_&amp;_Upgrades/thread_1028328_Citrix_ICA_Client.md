---
title: "Citrix ICA Client"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by SnackMasterX on 2009-01-02
Hello,

I have used ubuntu in the past but I want to use it on my laptop for work however there are a couple things I need to verify first otherwise I cannot use the ubuntu at work without the Citrix ICA client. I know I can get the client working however I need to ensure one important function can be preserved. My brother helped me find that I can still use local printers through citrix but now the biggest thing is I need to ensure I can transfer data between the citrix and the local machines. I did not see anywhere the ability to copy data between the local and citrix machine and if anyone has seen anything on this or knows how to do it please let me know, I really hate windows and have been having too many problems with the OS crashing, running slow and in general failing at life.

Thanks in Advance!

---

### Post by Stryker54 on 2009-01-05
SnackMasterX

I'm not a Citrix admin but have used Citrix from quite some time and believe that ability, to "copy and paste" between local and remote machines, is restricted at the Citrix server.  I'm unsure how configurable that option for the server admin and may have some limitations.

I'm in a similar situation and use Citrix to VPN into my client's network.  Their server only allows the copying and pasting of text between the local machine and the remote application or RDP session on a remote server.  No other objects, applications, or files can be copied or moved to the remote application or host.  My only recourse was to RDP onto the remote host and use IE or FTP to move or download files onto the remote machine.  It's not fantsy but it does work.

Stryker54

---

### Post by genesis2seven on 2009-05-21
It can be restricted at the server level but if it is not you have to select that as a preference when you first log in. You can select one way or the other and tell it not to ask you again. If that is the case then you'd have to check with your company's admin. Don't remember how to reset that preference once its set.

---

