---
title: "Disable Restart and Shut down"
date: 2008-10-23
forum: General Help
---

### Post by lsutiger on 2008-10-23
Hi all!
I have done this before, but forgot to take notes. Now I need to do it again: I want the only option on the logout menu to be Logoff (IE - remove shutdown/Restart/Hibernate/etc...)

I also need this only to effect certain users.

On my personal PC I have this implemented. I have all options available, but the other users only have logout.

I have been googling all afternoon, but can't find the answer again.
Any help will be greatly appreciated.

---

### Post by Pro-reason on 2008-10-23
I don't know about GDM, but with KDM you can choose whether users can shutdown or not.  If you remove their ability to do it, then it's only possible to shut down with “sudo shutdown -h now”.

---

### Post by cyfur01 on 2008-10-23
Manually edit /etc/gdm/gdm.conf, specifically:
```

...
# The following options specify how GDM system commands are supported.
#
# Specify which actions are displayed in the greeter.  Valid values are HALT,
# REBOOT, HIBERNATE, SUSPEND, and CUSTOM_CMD separated by semicolons.
SystemCommandsInMenu=HALT;REBOOT;HIBERNATE;SUSPEND;CUSTOM_CMD

# Specify which actions are supported by QUERY_LOGOUT_ACTION, SET_LOGOUT_ACTION
# and SET_SAFE_LOGOUT_ACTION.  Valid values are HALT, REBOOT, HIBERNATE, SUSPEND, and
# CUSTOM_CMD separated by semicolons.
AllowLogoutActions=HALT;REBOOT;HIBERNATE;SUSPEND;CUSTOM_CMD

# This feature is only functional if GDM is compiled with RBAC (Role Based
# Access Control) support.
# Specify the RBAC key used to determine if the user has permission to use
# the action via QUERY_LOGOUT_ACTION, SET_LOGOUT_ACTION and
# SET_SAFE_LOGOUT_ACTION.  The GDM GUI will only display the action if the
# "gdm" user has RBAC permissions to use the action.  RBAC keys for multiple
# actions can be specified by separating them by semicolons.  The format for
# each is "Action:RBAC key".  If an action is not specified, it is assumed
# all users have permission for this action.  For example:
# HALT:key.for.halt,REBOOT:key.for.reboot,[...]  
RBACSystemCommandKeys=
...

```

Also see: [http://ubuntuforums.org/showthread.php?t=927819]("http://ubuntuforums.org/showthread.php?t=927819")

---

### Post by ArielEnter on 2011-08-03
I followed the instructions from this thread and it worked great:
 

 [http://ubuntuforums.org/showthread.php?t=1670897&page=2](http://ubuntuforums.org/showthread.php?t=1670897&page=2)
 

 Is the same thing that prevents you to power off your computer while another user session is running.

---

