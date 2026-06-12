---
title: "evolution won't start after jaunty upgrade"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by baytuni on 2009-04-22
This is the shell when i tried to start evolution. I tried to uninstall evolution and evolution-exchange, basically all the software that have a "evolution" in its name and reinstalled them but did not work. Anybody has any ideas?

```
bop@hal:~$ evolution 
** (evolution:6178): DEBUG: EI: SHELL STARTUP

(evolution:6178): e-spinner.c-WARNING **: Cannot extract frame (0, 0) from the grid


(evolution:6178): e-spinner.c-WARNING **: Cannot extract frame (36, 0) from the grid


(evolution:6178): e-spinner.c-WARNING **: Cannot extract frame (72, 0) from the grid


(evolution:6178): e-spinner.c-WARNING **: Cannot extract frame (108, 0) from the grid


(evolution:6178): e-spinner.c-WARNING **: Cannot extract frame (144, 0) from the grid


(evolution:6178): e-spinner.c-WARNING **: Cannot extract frame (180, 0) from the grid


(evolution:6178): e-spinner.c-WARNING **: Cannot extract frame (216, 0) from the grid


(evolution:6178): e-spinner.c-WARNING **: Cannot extract frame (252, 0) from the grid

camel-imap-provider-Message: Unable to load summary: no such table: Calendar

camel-imap-provider-Message: Unable to load summary: no such table: Contacts

camel-imap-provider-Message: Unable to load summary: no such table: Journal

camel-imap-provider-Message: Unable to load summary: no such table: Junk E-Mail

camel-imap-provider-Message: Unable to load summary: no such table: Notes

camel-imap-provider-Message: Unable to load summary: no such table: Outbox

camel-imap-provider-Message: Unable to load summary: no such table: RSS Feeds

camel-imap-provider-Message: Unable to load summary: no such table: Sync Issues

camel-imap-provider-Message: Unable to load summary: no such table: Sync Issues/Conflicts

camel-imap-provider-Message: Unable to load summary: no such table: Sync Issues/Local Failures

camel-imap-provider-Message: Unable to load summary: no such table: Sync Issues/Server Failures

camel-imap-provider-Message: Unable to load summary: no such table: Tasks


```

---

### Post by rgnyman on 2009-04-23
I have also problems with evolution after jaunty upgrade. Evolution starts in offline and online mode but after I type in password for exchange server it aborts. To get it start again I have to delete the stored password.

e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-Exchange'
** (evolution:5819): DEBUG: mailto URL command: evolution %s
** (evolution:5819): DEBUG: mailto URL program: evolution
** (evolution:5819): DEBUG: EI: SHELL STARTUP

** (evolution:5819): WARNING **: Unexpected kerberos error -1765328164

** (evolution:5819): WARNING **: Unexpected kerberos error -1765328164

(evolution:5819): e-data-server-ui-WARNING **: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-Exchange'

GThread-ERROR **: file /build/buildd/glib2.0-2.20.1/gthread/gthread-posix.c: line 171 (g_mutex_free_posix_impl): error 'Device or resource busy' during 'pthread_mutex_destroy ((pthread_mutex_t *) mutex)'
aborting...

---

### Post by baytuni on 2009-04-23
I found out that the error messages may not be related with the problem. With compiz turned off I see same error messages but now evolution works as expected. So it is compiz problem.

---

### Post by CilGamir on 2009-04-24
Hi, 

When you say "with compiz turned off" what do you mean. 

I have no compiz.real process running, my visual effects is set to none. but evolution still wont start. 

It starts when running with --disable-eplugin, but that defeats the purpose, because i want to access exchange with it.

Thanks

---

### Post by satipera on 2009-04-24
My evolution was also broken after the upgrade. I noticed a few hours after the upgrade that there was small additional update. After I downloaded and installed this my evolution ran fine.

---

### Post by CilGamir on 2009-04-24
Yes, you're right.

At the time of posting the fix for evolution is part of unstable/proposed updates. You can enable those in your software sources application. 

Also, if evolution tells you that the url for your owa server might be wrong, be sure that you tell evolution not to try and connect through the regular proxy (if owa is accessable on your lan)

---

### Post by rgnyman on 2009-04-24
After evolution upgrade still facing problems. When I try authenticate to excahnge server evolution aborts with error.

** (evolution:5469): WARNING **: Unexpected kerberos error -1765328164

** (evolution:5469): WARNING **: Unexpected kerberos error -1765328164

GThread-ERROR **: file /build/buildd/glib2.0-2.20.1/gthread/gthread-posix.c: line 171 (g_mutex_free_posix_impl): error 'Device or resource busy' during 'pthread_mutex_destroy ((pthread_mutex_t *) mutex)'
aborting...

---

### Post by rgnyman on 2009-04-25
Finally got rid of the crash but still not able to authenticate to exchange server. The original server that I used to fetch packaged did not contain all needed files after changing the update source got all needed soap libraries.

I have to still verify with my 8.04 ubuntu laptop is there problem with the exchange server or 9.04.

---

### Post by rgnyman on 2009-04-25
It seems that there is some problem with jaynty evolution exchange authentication. I checked that our exchange server works fine with hardy evolution.

---

### Post by rgnyman on 2009-04-25
Hah. I had set system wide proxy at some point that prevented the authentication to exchange server. system->preferences->network proxy. Select direct and click apply system wide. Restart evolution, re-authenticate to exchange server, restart evolution and it works.

---

### Post by Indian Summer on 2009-06-30
> **rgnyman said:**
> Hah. I had set system wide proxy at some point that prevented the authentication to exchange server. system->preferences->network proxy. Select direct and click apply system wide. Restart evolution, re-authenticate to exchange server, restart evolution and it works.

:KS:KS:KS Ahhh...! Thank you! :KS:KS:KS 

That solved my problem. I've been struggling with this for quite a while now ...!

---

