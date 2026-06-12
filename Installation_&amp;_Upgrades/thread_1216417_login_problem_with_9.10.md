---
title: "login problem with 9.10"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by margu on 2009-07-18
I just upgraded my netbook from 9.04 to 9.10 and now I have difficulties in logging in to the system from gdm.
I was running the netbook-remix version of 9.04 and it was configured to log in to gnome without any login or passwd. It was also configured to start the wireless network without prompting for password.
After the upgrade to 9.10 I have to select a user at the gdm greeter, but the problem is that I get an error message when trying to do so.
gdm says:" error initiating conversation with authentication system - general failure" even before I get the chance to input a passwd.
If I switch to a terminal using ctrl+Alt+F2 I can log in and start X from the commandline.
In /var/auth.log I see the following:
 
Jul 18 14:34:00 AAO gdm-session-worker[2624]: PAM _pam_load_conf_file: unable to open /etc/pam.d/common-pamkeyring
Jul 18 14:34:00 AAO gdm-session-worker[2624]: PAM error loading (null)
Jul 18 14:34:00 AAO gdm-session-worker[2624]: PAM _pam_init_handlers: error reading /etc/pam.d/gdm
Jul 18 14:34:00 AAO gdm-session-worker[2624]: PAM _pam_init_handlers: [Critical error - immediate abort]
Jul 18 14:34:00 AAO gdm-session-worker[2624]: PAM error reading PAM configuration file
Jul 18 14:34:00 AAO gdm-session-worker[2624]: PAM pam_start: failed to initialize handlers


Does anybody have a clue what I can do to solve this?

---

### Post by margu on 2009-07-18
The problem was solved after commenting the following row in /etc/pam.d/gdm

@include common-pamkeyring

---

### Post by Mark Phelps on 2009-07-20
I hope you're ready to handle LOTS of problems.  

You do know that you just "upgraded" from a stable release to a highly unstable "alpha" release, right?  v9.10 isn't even going to be at the "beta" state for weeks yet.

---

### Post by margu on 2009-07-20
Yes, I know. I think it is fun to test new releases at an early stage and send bug reports to the developers.

---

