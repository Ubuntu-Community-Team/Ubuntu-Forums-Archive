---
title: "Mail-notification: installation"
date: 2008-09-27
forum: General Help
---

### Post by ojve on 2008-09-27
Hi!

I'm trying to install mail-notifier on Ubuntu 8.04. Everything works a charm, except starting the application. I used to have mail-notification 4.4(I think, the current available version in the ubuntu repositories anyway) installed before I tried the switch to 5.4.

. When I try running m-n, I get a popup saying:
Fatal error has occurred in Mail Notification
The default configuration has not been installed properly. Please check your Mail Notification installation the following messages:

nad the following terminal output:
** (mail-notification:12945): WARNING **: cannot find default value of configuration key "/apps/mail-notification/sounds/new-mail/enabled"
** (mail-notification:12945): WARNING **: cannot find default value of configuration key "/apps/mail-notification/sounds/new-mail/file"
** (mail-notification:12945): WARNING **: cannot find default value of configuration key "/apps/mail-notification/sounds/play-command"
** (mail-notification:12945): WARNING **: cannot find default value of configuration key "/apps/mail-notification/tooltip-mail-summary-limit"
** (mail-notification:12945): WARNING **: cannot find default value of configuration key "/apps/mail-notification/display-message-count"
** (mail-notification:12945): WARNING **: cannot find default value of configuration key "/apps/mail-notification/click-action-3"
** (mail-notification:12945): WARNING **: cannot find default value of configuration key "/apps/mail-notification/popups/expiration/delay-2"
** (mail-notification:12945): WARNING **: cannot find default value of configuration key "/apps/mail-notification/popups/limit"
** (mail-notification:12945): WARNING **: cannot find default value of configuration key "/apps/mail-notification/fallback-charsets"
** (mail-notification:12945): WARNING **: cannot find default value of configuration key "/apps/mail-notification/popups/expiration/delay-2"
** (mail-notification:12945): WARNING **: cannot find default value of configuration key "/apps/mail-notification/messages-considered-as-read"

This is my configuration output, if it's any help:
Compiler options:

    cc:                      cc
    cflags:                  -O2
    cppflags:
    ldflags:
    libs:
    cc-dependency-tracking:  yes

  Installation options:

    destdir:
    prefix:                  /usr
    bindir:                  $prefix/bin
    libdir:                  $prefix/lib
    libexecdir:              $prefix/libexec
    datadir:                 $prefix/share
    sysconfdir:              $prefix/etc
    localstatedir:           $prefix/var
    data-mode:               0644
    data-owner:
    data-group:
    program-mode:            0755
    program-owner:
    program-group:
    library-mode:            0644
    library-owner:
    library-group:
    gconf-config-source:     xml:merged:/etc/gconf/gconf.xml.defaults
    gconf-schemas-dir:       $datadir/gconf/schemas
    install-gconf-schemas:   yes
    help-dir:                $datadir/gnome/help
    omf-dir:                 /usr/share/omf
    scrollkeeper-dir:        /var/lib/scrollkeeper
    evolution-plugin-dir:    /usr/lib/evolution/2.22/plugins

  External programs:

    msgfmt:                  /usr/bin/msgfmt
    perl:                    /usr/bin/perl
    gconftool-2:             /usr/bin/gconftool-2
    scrollkeeper-preinstall: /usr/bin/scrollkeeper-preinstall
    scrollkeeper-update:     /usr/bin/scrollkeeper-update
    dbus-binding-tool:       /usr/bin/dbus-binding-tool
    gob2:                    /usr/bin/gob2

  Mailbox backends:

    evolution:               yes
    gmail:                   yes
    hotmail:                 yes
    imap:                    yes
    maildir:                 yes
    mbox:                    yes
    mh:                      yes
    mozilla:                 yes
    pop3:                    yes
    sylpheed:                yes
    yahoo:                   yes

  IMAP and POP3 features:

    ipv6:                    yes
    sasl:                    yes
    ssl:                     yes


Would be grateful for any help!

THX
//T

---

### Post by cariboo on 2008-09-27
The error message pretty well tells you what the problem is. The program is looking for /apps/mail-notification directory and it can't find it.

You could try creating and populating the directory in / to see if it works.

Jim

---

### Post by ojve on 2008-09-27
Yeah, well I understand why it doesn't work, I just have no idea what to do about it. I have no clue as to what put in the files.And am I really supposed to create a new directory in the root of the filesystem? It seems kind of odd.

It seems to me like something is missing from the installation process...

EDIT: I tried creating a file called : "/apps/mail-notification/messages-considered-as-read" with the content: "false". no luck

---

