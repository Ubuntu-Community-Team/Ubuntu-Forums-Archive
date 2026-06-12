---
title: "SSH server security"
date: 2008-08-24
forum: General Help
---

### Post by illumi on 2008-08-24
I launched my ssh server today to be online all the time and it's getting bombarded by log in attempts.. here is a two minute snapshot from the auth.log file:

```

Aug 24 18:47:59 moo-top sshd[6839]: Failed password for root from 61.16.156.148 port 37145 ssh2
Aug 24 18:48:01 moo-top sshd[6841]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:48:01 moo-top sshd[6841]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148  user=root
Aug 24 18:48:03 moo-top sshd[6841]: Failed password for root from 61.16.156.148 port 37275 ssh2
Aug 24 18:48:05 moo-top sshd[6843]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:48:05 moo-top sshd[6843]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148  user=root
Aug 24 18:48:07 moo-top sshd[6843]: Failed password for root from 61.16.156.148 port 37402 ssh2
Aug 24 18:48:09 moo-top sshd[6845]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148  user=root
Aug 24 18:48:11 moo-top sshd[6845]: Failed password for root from 61.16.156.148 port 37541 ssh2
Aug 24 18:48:13 moo-top sshd[6847]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:48:13 moo-top sshd[6847]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148  user=root
Aug 24 18:48:15 moo-top sshd[6847]: Failed password for root from 61.16.156.148 port 36135 ssh2
Aug 24 18:48:17 moo-top sshd[6849]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:48:17 moo-top sshd[6849]: Invalid user admin from 61.16.156.148
Aug 24 18:48:17 moo-top sshd[6849]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:48:19 moo-top sshd[6849]: Failed password for invalid user admin from 61.16.156.148 port 36262 ssh2
Aug 24 18:48:21 moo-top sshd[6851]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:48:21 moo-top sshd[6851]: Invalid user admin from 61.16.156.148
Aug 24 18:48:21 moo-top sshd[6851]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:48:21 moo-top sshd[6851]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:48:23 moo-top sshd[6851]: Failed password for invalid user admin from 61.16.156.148 port 36381 ssh2
Aug 24 18:48:25 moo-top sshd[6853]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:48:25 moo-top sshd[6853]: Invalid user admin from 61.16.156.148
Aug 24 18:48:25 moo-top sshd[6853]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:48:25 moo-top sshd[6853]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:48:26 moo-top sshd[6853]: Failed password for invalid user admin from 61.16.156.148 port 36514 ssh2
Aug 24 18:48:28 moo-top sshd[6855]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:48:28 moo-top sshd[6855]: Invalid user admin from 61.16.156.148
Aug 24 18:48:28 moo-top sshd[6855]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:48:28 moo-top sshd[6855]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:48:30 moo-top sshd[6855]: Failed password for invalid user admin from 61.16.156.148 port 36637 ssh2
Aug 24 18:48:32 moo-top sshd[6857]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:48:34 moo-top sshd[6857]: Failed password for root from 61.16.156.148 port 36760 ssh2
Aug 24 18:48:36 moo-top sshd[6859]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:48:36 moo-top sshd[6859]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148  user=root
Aug 24 18:48:38 moo-top sshd[6859]: Failed password for root from 61.16.156.148 port 36891 ssh2
Aug 24 18:48:40 moo-top sshd[6861]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:48:40 moo-top sshd[6861]: Invalid user test from 61.16.156.148
Aug 24 18:48:40 moo-top sshd[6861]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:48:40 moo-top sshd[6861]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:48:44 moo-top sshd[6863]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:48:44 moo-top sshd[6863]: Invalid user test from 61.16.156.148
Aug 24 18:48:44 moo-top sshd[6863]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:48:44 moo-top sshd[6863]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:48:46 moo-top sshd[6863]: Failed password for invalid user test from 61.16.156.148 port 37150 ssh2
Aug 24 18:48:48 moo-top sshd[6865]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:48:48 moo-top sshd[6865]: Invalid user webmaster from 61.16.156.148
Aug 24 18:48:48 moo-top sshd[6865]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:48:48 moo-top sshd[6865]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:48:50 moo-top sshd[6865]: Failed password for invalid user webmaster from 61.16.156.148 port 37276 ssh2
Aug 24 18:48:52 moo-top sshd[6867]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:48:52 moo-top sshd[6867]: Invalid user username from 61.16.156.148
Aug 24 18:48:52 moo-top sshd[6867]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:48:52 moo-top sshd[6867]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:48:54 moo-top sshd[6867]: Failed password for invalid user username from 61.16.156.148 port 37415 ssh2
Aug 24 18:48:56 moo-top sshd[6869]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:48:56 moo-top sshd[6869]: Invalid user user from 61.16.156.148
Aug 24 18:48:56 moo-top sshd[6869]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:48:56 moo-top sshd[6869]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:48:58 moo-top sshd[6869]: Failed password for invalid user user from 61.16.156.148 port 37546 ssh2
Aug 24 18:49:00 moo-top sshd[6871]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:49:00 moo-top sshd[6871]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148  user=root
Aug 24 18:49:02 moo-top sshd[6871]: Failed password for root from 61.16.156.148 port 37674 ssh2
Aug 24 18:49:04 moo-top sshd[6873]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:49:04 moo-top sshd[6873]: Invalid user admin from 61.16.156.148
Aug 24 18:49:04 moo-top sshd[6873]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:49:04 moo-top sshd[6873]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:49:07 moo-top sshd[6873]: Failed password for invalid user admin from 61.16.156.148 port 37819 ssh2
Aug 24 18:49:09 moo-top sshd[6875]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:49:09 moo-top sshd[6875]: Invalid user test from 61.16.156.148
Aug 24 18:49:09 moo-top sshd[6875]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:49:09 moo-top sshd[6875]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:49:11 moo-top sshd[6875]: Failed password for invalid user test from 61.16.156.148 port 37968 ssh2
Aug 24 18:49:13 moo-top sshd[6877]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:49:13 moo-top sshd[6877]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148  user=root
Aug 24 18:49:15 moo-top sshd[6877]: Failed password for root from 61.16.156.148 port 38111 ssh2
Aug 24 18:49:17 moo-top sshd[6879]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:49:17 moo-top sshd[6879]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148  user=root
Aug 24 18:49:21 moo-top sshd[6881]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:49:21 moo-top sshd[6881]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148  user=root
Aug 24 18:49:23 moo-top sshd[6881]: Failed password for root from 61.16.156.148 port 38365 ssh2
Aug 24 18:49:25 moo-top sshd[6883]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:49:25 moo-top sshd[6883]: Invalid user danny from 61.16.156.148
Aug 24 18:49:25 moo-top sshd[6883]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:49:25 moo-top sshd[6883]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:49:27 moo-top sshd[6883]: Failed password for invalid user danny from 61.16.156.148 port 38493 ssh2
Aug 24 18:49:29 moo-top sshd[6885]: Invalid user alex from 61.16.156.148
Aug 24 18:49:29 moo-top sshd[6885]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:49:29 moo-top sshd[6885]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:49:31 moo-top sshd[6885]: Failed password for invalid user alex from 61.16.156.148 port 38615 ssh2
Aug 24 18:49:33 moo-top sshd[6887]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:49:33 moo-top sshd[6887]: Invalid user brett from 61.16.156.148
Aug 24 18:49:33 moo-top sshd[6887]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:49:33 moo-top sshd[6887]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:49:35 moo-top sshd[6887]: Failed password for invalid user brett from 61.16.156.148 port 38752 ssh2
Aug 24 18:49:37 moo-top sshd[6889]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:49:37 moo-top sshd[6889]: Invalid user mike from 61.16.156.148
Aug 24 18:49:37 moo-top sshd[6889]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:49:37 moo-top sshd[6889]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:49:39 moo-top sshd[6889]: Failed password for invalid user mike from 61.16.156.148 port 38885 ssh2
Aug 24 18:49:41 moo-top sshd[6891]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:49:41 moo-top sshd[6891]: Invalid user alan from 61.16.156.148
Aug 24 18:49:41 moo-top sshd[6891]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:49:41 moo-top sshd[6891]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:49:43 moo-top sshd[6891]: Failed password for invalid user alan from 61.16.156.148 port 39000 ssh2
Aug 24 18:49:45 moo-top sshd[6893]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:49:45 moo-top sshd[6893]: Invalid user data from 61.16.156.148
Aug 24 18:49:45 moo-top sshd[6893]: pam_unix(sshd:auth): check pass; user unknown
Aug 24 18:49:45 moo-top sshd[6893]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148
Aug 24 18:49:47 moo-top sshd[6893]: Failed password for invalid user data from 61.16.156.148 port 39144 ssh2
Aug 24 18:49:57 moo-top sshd[6895]: reverse mapping checking getaddrinfo for del-static-148-156-16-61.direct.net.in [61.16.156.148] failed - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 18:49:57 moo-top sshd[6895]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.16.156.148  user=www-data
Aug 24 18:49:59 moo-top sshd[6895]: Failed password for www-data from 61.16.156.148 port 39270 ssh2

```

Is there anything I can do about this? Is there a tally that would ban the connecting host after 3 invalid connection attempts or something similar?

---

### Post by bthoward on 2008-08-24
Open a console and type "sudo apt-get install sshguard" or click this link [apt://sshguard]("apt://sshguard")

---

### Post by bodhi.zazen on 2008-08-24
Yes, the ssh server gets hammered. As you can see these attempts are targeting root, a good reason to use sudo rather the su ... (root account locked in Ubuntu).

I suggest you look at :

[uwiki]AdvancedOpenSSHif[/uwiki]

You can install denyhosts, use sshguard, or write rules for iptables, but if you lock down the ssh server, use keys, and change the port you should be fine.

If you think that is bad, install snort ...

Most of these things are script kiddies and they move on pretty fast. If I get hammered by any particular IP, however, ban them :twisted:

You can do this in several ways, Ubuntu uses UFW by default :

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw#Advanced%20Blocking%20Rules](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw#Advanced%20Blocking%20Rules)

---

### Post by Joeb454 on 2008-08-24
Are you running it over port 22?

---

### Post by bthoward on 2008-08-24
If you are you can edit your /etc/ssh/sshd-config file and change the port that it operates on.  Then when you want to connect to the box you use ssh <box name> -p<port num>.  Running SSH on a non standard port is one of the best first layers of protection and its something I do rigth from the get go on any of my server boxes.  

Actually I move it on my laptop too...

---

### Post by illumi on 2008-08-24
Thanks for your help folks, yes it's on port 22. after some more research I've installed fail2ban(seems to be a neat app) as it covers ftp and webmin attacks also. changing the port number isn't really an option sadly as I can only connect out on port 22 from college :(

---

### Post by bthoward on 2008-08-24
BTw SSHGuard does other protocols as well...  Glad all worked out for you though.

---

### Post by illumi on 2008-08-25
Seems to work, although my auth.log is flooded with 'cron' logs like these every 10 minutes:

```

Aug 25 12:39:01 moo-top CRON[8093]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 25 12:39:01 moo-top CRON[8093]: pam_unix(cron:session): session closed for user root
Aug 25 13:09:01 moo-top CRON[8110]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 25 13:09:01 moo-top CRON[8110]: pam_unix(cron:session): session closed for user root
Aug 25 13:17:01 moo-top CRON[8112]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 25 13:17:01 moo-top CRON[8112]: pam_unix(cron:session): session closed for user root

```

what is that all about? :confused::confused:

---

### Post by kpatz on 2008-08-25
> **illumi said:**
> Seems to work, although my auth.log is flooded with 'cron' logs like these every 10 minutes.

what is that all about? :confused::confused:You have cron jobs that run as root, so cron "logs in" as root in order to run those jobs.  There's nothing to worry about.

---

