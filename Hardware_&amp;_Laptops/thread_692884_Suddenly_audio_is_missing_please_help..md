---
title: "Suddenly audio is missing please help."
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by SniperZero on 2008-02-10
I am running kubuntu gutsy. Onboard sound Nvidia ac97, I run kde3 but have kde4 installed as well.

My sound was working all fine until suddenly today when I turned my computer back on from been away the last day. Few days before hand there was few updates that I just let all update and sound was fine so I am assuming when rebooting it stopped it.

Here is my latest dpkg log of what was updated. As you can see at the bottom I have retried to reinstall xine/alsa.
```

2008-02-07 11:09:17 startup archives unpack
2008-02-07 11:09:31 upgrade libkonq5-templates 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:31 status half-configured libkonq5-templates 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:31 status unpacked libkonq5-templates 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:31 status half-installed libkonq5-templates 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:31 status half-installed libkonq5-templates 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:31 status unpacked libkonq5-templates 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:31 status unpacked libkonq5-templates 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:31 upgrade libkonq5 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:31 status half-configured libkonq5 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:31 status unpacked libkonq5 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:31 status half-installed libkonq5 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:31 status half-installed libkonq5 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:31 status unpacked libkonq5 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:31 status unpacked libkonq5 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:31 upgrade dolphin-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:31 status half-configured dolphin-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:31 status unpacked dolphin-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:31 status half-installed dolphin-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:32 status half-installed dolphin-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:32 status unpacked dolphin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:32 status unpacked dolphin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:32 upgrade kappfinder-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:32 status half-configured kappfinder-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:32 status unpacked kappfinder-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:32 status half-installed kappfinder-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:32 status half-installed kappfinder-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:32 status unpacked kappfinder-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:33 status unpacked kappfinder-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:33 upgrade kdebase-bin-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:33 status half-configured kdebase-bin-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:33 status unpacked kdebase-bin-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:33 status half-installed kdebase-bin-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:33 status half-installed kdebase-bin-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:33 status unpacked kdebase-bin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:33 status unpacked kdebase-bin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:33 upgrade kdebase-data-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:33 status half-configured kdebase-data-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:33 status unpacked kdebase-data-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:33 status half-installed kdebase-data-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:33 status half-installed kdebase-data-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:33 status unpacked kdebase-data-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:33 status unpacked kdebase-data-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:33 upgrade kdepasswd-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:33 status half-configured kdepasswd-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:33 status unpacked kdepasswd-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:33 status half-installed kdepasswd-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:33 status half-installed kdepasswd-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:34 status unpacked kdepasswd-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:34 status unpacked kdepasswd-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:34 upgrade kfind-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:34 status half-configured kfind-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:34 status unpacked kfind-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:34 status half-installed kfind-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:34 status half-installed kfind-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:34 status unpacked kfind-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:34 status unpacked kfind-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:34 upgrade konqueror-nsplugins-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:34 status half-configured konqueror-nsplugins-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:34 status unpacked konqueror-nsplugins-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:34 status half-installed konqueror-nsplugins-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:34 status half-installed konqueror-nsplugins-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:34 status unpacked konqueror-nsplugins-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:34 status unpacked konqueror-nsplugins-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:34 upgrade konqueror-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:34 status half-configured konqueror-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:34 status unpacked konqueror-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:34 status half-installed konqueror-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:34 status half-installed konqueror-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:34 status unpacked konqueror-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:35 status unpacked konqueror-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:35 upgrade konsole-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:35 status half-configured konsole-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:35 status unpacked konsole-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:35 status half-installed konsole-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:35 status half-installed konsole-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:35 status unpacked konsole-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:35 status unpacked konsole-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:35 upgrade kwrite-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:35 status half-configured kwrite-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:35 status unpacked kwrite-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:35 status half-installed kwrite-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:35 status half-installed kwrite-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:35 status unpacked kwrite-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:35 status unpacked kwrite-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:35 upgrade kdebase-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:35 status half-configured kdebase-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:35 status unpacked kdebase-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:35 status half-installed kdebase-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:35 status half-installed kdebase-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-07 11:09:35 status unpacked kdebase-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:35 status unpacked kdebase-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:36 startup packages configure
2008-02-07 11:09:36 configure libkonq5-templates 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:36 status unpacked libkonq5-templates 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:36 status half-configured libkonq5-templates 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:36 status installed libkonq5-templates 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:36 configure libkonq5 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:36 status unpacked libkonq5 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:36 status half-configured libkonq5 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:36 status installed libkonq5 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:36 status triggers-pending libc6 2.6.1-1ubuntu10
2008-02-07 11:09:36 configure dolphin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:36 status unpacked dolphin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:36 status half-configured dolphin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:40 status installed dolphin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:40 configure kappfinder-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:40 status unpacked kappfinder-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:40 status half-configured kappfinder-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:40 status installed kappfinder-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:40 configure kdebase-data-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:40 status unpacked kdebase-data-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:40 status half-configured kdebase-data-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:40 status installed kdebase-data-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 configure kdebase-bin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status unpacked kdebase-bin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status half-configured kdebase-bin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status installed kdebase-bin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 configure kdepasswd-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status unpacked kdepasswd-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status half-configured kdepasswd-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status installed kdepasswd-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 configure kfind-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status unpacked kfind-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status half-configured kfind-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status installed kfind-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 configure konqueror-nsplugins-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status unpacked konqueror-nsplugins-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status half-configured konqueror-nsplugins-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status installed konqueror-nsplugins-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 configure konqueror-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status unpacked konqueror-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status half-configured konqueror-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status installed konqueror-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 configure konsole-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status unpacked konsole-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:41 status half-configured konsole-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:42 status installed konsole-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:42 configure kwrite-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:42 status unpacked kwrite-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:42 status half-configured kwrite-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:42 status installed kwrite-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:42 configure kdebase-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:42 status unpacked kdebase-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:42 status half-configured kdebase-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:42 status installed kdebase-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-07 11:09:42 trigproc libc6 2.6.1-1ubuntu10 2.6.1-1ubuntu10
2008-02-07 11:09:42 status half-configured libc6 2.6.1-1ubuntu10
2008-02-07 11:09:55 status installed libc6 2.6.1-1ubuntu10
2008-02-08 10:35:43 startup archives unpack
2008-02-08 10:35:58 upgrade libplasma1 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:35:58 status half-configured libplasma1 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:35:58 status unpacked libplasma1 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:35:58 status half-installed libplasma1 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:35:58 status half-installed libplasma1 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:35:58 status unpacked libplasma1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:35:58 status unpacked libplasma1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:35:58 upgrade kdebase-workspace-data 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:35:58 status half-configured kdebase-workspace-data 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:35:58 status unpacked kdebase-workspace-data 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:35:58 status half-installed kdebase-workspace-data 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:02 status half-installed kdebase-workspace-data 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:03 status unpacked kdebase-workspace-data 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:04 status unpacked kdebase-workspace-data 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:04 upgrade ksysguard-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:04 status half-configured ksysguard-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:04 status unpacked ksysguard-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:04 status half-installed ksysguard-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:05 status half-installed ksysguard-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:05 status unpacked ksysguard-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:05 status unpacked ksysguard-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:05 upgrade ksysguardd-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:05 status half-configured ksysguardd-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:05 status unpacked ksysguardd-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:05 status half-installed ksysguardd-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:06 status half-installed ksysguardd-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:06 status unpacked ksysguardd-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:06 status unpacked ksysguardd-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:06 upgrade kdebase-workspace-bin 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:06 status half-configured kdebase-workspace-bin 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:06 status unpacked kdebase-workspace-bin 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:06 status half-installed kdebase-workspace-bin 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:07 status half-installed kdebase-workspace-bin 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:07 status unpacked kdebase-workspace-bin 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:08 status unpacked kdebase-workspace-bin 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:08 upgrade klipper-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:08 status half-configured klipper-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:08 status unpacked klipper-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:08 status half-installed klipper-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:08 status half-installed klipper-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:08 status unpacked klipper-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:08 status unpacked klipper-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:08 upgrade kwin-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:08 status half-configured kwin-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:09 status unpacked kwin-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:09 status half-installed kwin-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:09 status half-installed kwin-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:09 status unpacked kwin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:09 status unpacked kwin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:10 upgrade systemsettings-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:10 status half-configured systemsettings-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:10 status unpacked systemsettings-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:10 status half-installed systemsettings-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:10 status half-installed systemsettings-kde4 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:10 status unpacked systemsettings-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:10 status unpacked systemsettings-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:10 upgrade kdebase-workspace 4:4.0.1-0ubuntu1~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:10 status half-configured kdebase-workspace 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:10 status unpacked kdebase-workspace 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:10 status half-installed kdebase-workspace 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:10 status half-installed kdebase-workspace 4:4.0.1-0ubuntu1~gutsy1~ppa1
2008-02-08 10:36:10 status unpacked kdebase-workspace 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:10 status unpacked kdebase-workspace 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:11 startup packages configure
2008-02-08 10:36:11 configure ksysguardd-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:11 status unpacked ksysguardd-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:11 status half-configured ksysguardd-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:11 status installed ksysguardd-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:11 configure kdebase-workspace-data 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:11 status unpacked kdebase-workspace-data 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:11 status half-configured kdebase-workspace-data 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:14 status installed kdebase-workspace-data 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:14 configure klipper-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:14 status unpacked klipper-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:14 status half-configured klipper-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:14 status installed klipper-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:14 configure kwin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:14 status unpacked kwin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:14 status half-configured kwin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status installed kwin-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status triggers-pending libc6 2.6.1-1ubuntu10
2008-02-08 10:36:15 configure systemsettings-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status unpacked systemsettings-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status half-configured systemsettings-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status installed systemsettings-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 configure libplasma1 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status unpacked libplasma1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status half-configured libplasma1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status installed libplasma1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 configure ksysguard-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status unpacked ksysguard-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status half-configured ksysguard-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status installed ksysguard-kde4 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 configure kdebase-workspace-bin 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status unpacked kdebase-workspace-bin 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status half-configured kdebase-workspace-bin 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status installed kdebase-workspace-bin 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 configure kdebase-workspace 4:4.0.1-0ubuntu2~gutsy1~ppa1 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status unpacked kdebase-workspace 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status half-configured kdebase-workspace 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 status installed kdebase-workspace 4:4.0.1-0ubuntu2~gutsy1~ppa1
2008-02-08 10:36:15 trigproc libc6 2.6.1-1ubuntu10 2.6.1-1ubuntu10
2008-02-08 10:36:15 status half-configured libc6 2.6.1-1ubuntu10
2008-02-08 10:36:33 status installed libc6 2.6.1-1ubuntu10
2008-02-09 12:49:22 startup archives unpack
2008-02-09 12:49:36 install camorama <none> 0.18-2ubuntu2
2008-02-09 12:49:36 status half-installed camorama 0.18-2ubuntu2
2008-02-09 12:49:39 status unpacked camorama 0.18-2ubuntu2
2008-02-09 12:49:39 status unpacked camorama 0.18-2ubuntu2
2008-02-09 12:49:39 install gksu <none> 2.0.0-4ubuntu2
2008-02-09 12:49:39 status half-installed gksu 2.0.0-4ubuntu2
2008-02-09 12:49:39 status unpacked gksu 2.0.0-4ubuntu2
2008-02-09 12:49:39 status unpacked gksu 2.0.0-4ubuntu2
2008-02-09 12:49:39 install python2.4-minimal <none> 2.4.4-6ubuntu4
2008-02-09 12:49:39 status half-installed python2.4-minimal 2.4.4-6ubuntu4
2008-02-09 12:49:40 status unpacked python2.4-minimal 2.4.4-6ubuntu4
2008-02-09 12:49:40 status unpacked python2.4-minimal 2.4.4-6ubuntu4
2008-02-09 12:49:40 install python2.4 <none> 2.4.4-6ubuntu4
2008-02-09 12:49:40 status half-installed python2.4 2.4.4-6ubuntu4
2008-02-09 12:49:41 status unpacked python2.4 2.4.4-6ubuntu4
2008-02-09 12:49:41 status unpacked python2.4 2.4.4-6ubuntu4
2008-02-09 12:49:41 install python-xml <none> 0.8.4-8ubuntu1
2008-02-09 12:49:41 status half-installed python-xml 0.8.4-8ubuntu1
2008-02-09 12:49:42 status unpacked python-xml 0.8.4-8ubuntu1
2008-02-09 12:49:42 status unpacked python-xml 0.8.4-8ubuntu1
2008-02-09 12:49:42 install easycam2 <none> 1.99-10c
2008-02-09 12:49:42 status half-installed easycam2 1.99-10c
2008-02-09 12:49:43 status unpacked easycam2 1.99-10c
2008-02-09 12:49:43 status unpacked easycam2 1.99-10c
2008-02-09 12:49:44 startup packages configure
2008-02-09 12:49:44 configure camorama 0.18-2ubuntu2 0.18-2ubuntu2
2008-02-09 12:49:44 status unpacked camorama 0.18-2ubuntu2
2008-02-09 12:49:44 status half-configured camorama 0.18-2ubuntu2
2008-02-09 12:49:53 status installed camorama 0.18-2ubuntu2
2008-02-09 12:49:53 configure gksu 2.0.0-4ubuntu2 2.0.0-4ubuntu2
2008-02-09 12:49:53 status unpacked gksu 2.0.0-4ubuntu2
2008-02-09 12:49:53 status half-configured gksu 2.0.0-4ubuntu2
2008-02-09 12:49:53 status installed gksu 2.0.0-4ubuntu2
2008-02-09 12:49:53 configure python2.4-minimal 2.4.4-6ubuntu4 2.4.4-6ubuntu4
2008-02-09 12:49:53 status unpacked python2.4-minimal 2.4.4-6ubuntu4
2008-02-09 12:49:53 status unpacked python2.4-minimal 2.4.4-6ubuntu4
2008-02-09 12:49:53 status half-configured python2.4-minimal 2.4.4-6ubuntu4
2008-02-09 12:50:12 status installed python2.4-minimal 2.4.4-6ubuntu4
2008-02-09 12:50:12 configure python2.4 2.4.4-6ubuntu4 2.4.4-6ubuntu4
2008-02-09 12:50:12 status unpacked python2.4 2.4.4-6ubuntu4
2008-02-09 12:50:12 status half-configured python2.4 2.4.4-6ubuntu4
2008-02-09 12:50:17 status installed python2.4 2.4.4-6ubuntu4
2008-02-09 12:50:17 status triggers-pending libc6 2.6.1-1ubuntu10
2008-02-09 12:50:17 configure python-xml 0.8.4-8ubuntu1 0.8.4-8ubuntu1
2008-02-09 12:50:17 status unpacked python-xml 0.8.4-8ubuntu1
2008-02-09 12:50:17 status half-configured python-xml 0.8.4-8ubuntu1
2008-02-09 12:50:19 status installed python-xml 0.8.4-8ubuntu1
2008-02-09 12:50:19 configure easycam2 1.99-10c 1.99-10c
2008-02-09 12:50:19 status unpacked easycam2 1.99-10c
2008-02-09 12:50:19 status half-configured easycam2 1.99-10c
2008-02-09 12:50:19 status installed easycam2 1.99-10c
2008-02-09 12:50:19 trigproc libc6 2.6.1-1ubuntu10 2.6.1-1ubuntu10
2008-02-09 12:50:19 status half-configured libc6 2.6.1-1ubuntu10
2008-02-09 12:50:32 status installed libc6 2.6.1-1ubuntu10
2008-02-10 19:48:39 startup archives unpack
2008-02-10 19:48:56 upgrade libarts1-xine 4:3.5.8-0ubuntu1 4:3.5.8-0ubuntu1
2008-02-10 19:48:56 status half-configured libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 19:48:56 status unpacked libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 19:48:56 status half-installed libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 19:48:57 status half-installed libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 19:48:57 status unpacked libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 19:48:57 status unpacked libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 19:48:57 upgrade libxine1 1.1.7-1ubuntu1 1.1.7-1ubuntu1
2008-02-10 19:48:57 status half-configured libxine1 1.1.7-1ubuntu1
2008-02-10 19:48:57 status unpacked libxine1 1.1.7-1ubuntu1
2008-02-10 19:48:57 status half-installed libxine1 1.1.7-1ubuntu1
2008-02-10 19:48:58 status half-installed libxine1 1.1.7-1ubuntu1
2008-02-10 19:48:58 status unpacked libxine1 1.1.7-1ubuntu1
2008-02-10 19:48:58 status unpacked libxine1 1.1.7-1ubuntu1
2008-02-10 19:48:59 startup packages configure
2008-02-10 19:48:59 configure libxine1 1.1.7-1ubuntu1 1.1.7-1ubuntu1
2008-02-10 19:48:59 status unpacked libxine1 1.1.7-1ubuntu1
2008-02-10 19:48:59 status half-configured libxine1 1.1.7-1ubuntu1
2008-02-10 19:48:59 status installed libxine1 1.1.7-1ubuntu1
2008-02-10 19:48:59 status triggers-pending libc6 2.6.1-1ubuntu10
2008-02-10 19:48:59 configure libarts1-xine 4:3.5.8-0ubuntu1 4:3.5.8-0ubuntu1
2008-02-10 19:48:59 status unpacked libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 19:48:59 status half-configured libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 19:48:59 status installed libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 19:48:59 trigproc libc6 2.6.1-1ubuntu10 2.6.1-1ubuntu10
2008-02-10 19:48:59 status half-configured libc6 2.6.1-1ubuntu10
2008-02-10 19:49:20 status installed libc6 2.6.1-1ubuntu10
2008-02-10 20:02:04 startup archives unpack
2008-02-10 20:02:20 upgrade alsa-base 1.0.14-1ubuntu2 1.0.14-1ubuntu2
2008-02-10 20:02:20 status half-configured alsa-base 1.0.14-1ubuntu2
2008-02-10 20:02:20 status unpacked alsa-base 1.0.14-1ubuntu2
2008-02-10 20:02:20 status half-installed alsa-base 1.0.14-1ubuntu2
2008-02-10 20:02:20 status half-installed alsa-base 1.0.14-1ubuntu2
2008-02-10 20:02:21 status unpacked alsa-base 1.0.14-1ubuntu2
2008-02-10 20:02:21 status unpacked alsa-base 1.0.14-1ubuntu2
2008-02-10 20:02:21 startup packages configure
2008-02-10 20:02:21 configure alsa-base 1.0.14-1ubuntu2 1.0.14-1ubuntu2
2008-02-10 20:02:21 status unpacked alsa-base 1.0.14-1ubuntu2
2008-02-10 20:02:21 status unpacked alsa-base 1.0.14-1ubuntu2
2008-02-10 20:02:22 status unpacked alsa-base 1.0.14-1ubuntu2
2008-02-10 20:02:22 status unpacked alsa-base 1.0.14-1ubuntu2
2008-02-10 20:02:22 status half-configured alsa-base 1.0.14-1ubuntu2
2008-02-10 20:02:22 status installed alsa-base 1.0.14-1ubuntu2
2008-02-10 20:15:38 startup archives unpack
2008-02-10 20:15:54 upgrade libasound2 1.0.14-1ubuntu8 1.0.14-1ubuntu8
2008-02-10 20:15:54 status half-configured libasound2 1.0.14-1ubuntu8
2008-02-10 20:15:54 status unpacked libasound2 1.0.14-1ubuntu8
2008-02-10 20:15:54 status half-installed libasound2 1.0.14-1ubuntu8
2008-02-10 20:15:54 status half-installed libasound2 1.0.14-1ubuntu8
2008-02-10 20:15:54 status unpacked libasound2 1.0.14-1ubuntu8
2008-02-10 20:15:54 status unpacked libasound2 1.0.14-1ubuntu8
2008-02-10 20:15:54 upgrade linux-sound-base 1.0.14-1ubuntu2 1.0.14-1ubuntu2
2008-02-10 20:15:54 status half-configured linux-sound-base 1.0.14-1ubuntu2
2008-02-10 20:15:54 status unpacked linux-sound-base 1.0.14-1ubuntu2
2008-02-10 20:15:54 status half-installed linux-sound-base 1.0.14-1ubuntu2
2008-02-10 20:15:55 status half-installed linux-sound-base 1.0.14-1ubuntu2
2008-02-10 20:15:55 status unpacked linux-sound-base 1.0.14-1ubuntu2
2008-02-10 20:15:55 status unpacked linux-sound-base 1.0.14-1ubuntu2
2008-02-10 20:15:55 upgrade libesd-alsa0 0.2.38-0ubuntu4 0.2.38-0ubuntu4
2008-02-10 20:15:55 status half-configured libesd-alsa0 0.2.38-0ubuntu4
2008-02-10 20:15:55 status unpacked libesd-alsa0 0.2.38-0ubuntu4
2008-02-10 20:15:55 status half-installed libesd-alsa0 0.2.38-0ubuntu4
2008-02-10 20:15:55 status half-installed libesd-alsa0 0.2.38-0ubuntu4
2008-02-10 20:15:55 status unpacked libesd-alsa0 0.2.38-0ubuntu4
2008-02-10 20:15:55 status unpacked libesd-alsa0 0.2.38-0ubuntu4
2008-02-10 20:15:56 startup packages configure
2008-02-10 20:15:56 configure libasound2 1.0.14-1ubuntu8 1.0.14-1ubuntu8
2008-02-10 20:15:56 status unpacked libasound2 1.0.14-1ubuntu8
2008-02-10 20:15:57 status half-configured libasound2 1.0.14-1ubuntu8
2008-02-10 20:15:58 status installed libasound2 1.0.14-1ubuntu8
2008-02-10 20:15:58 status triggers-pending libc6 2.6.1-1ubuntu10
2008-02-10 20:15:58 configure linux-sound-base 1.0.14-1ubuntu2 1.0.14-1ubuntu2
2008-02-10 20:15:58 status unpacked linux-sound-base 1.0.14-1ubuntu2
2008-02-10 20:15:58 status half-configured linux-sound-base 1.0.14-1ubuntu2
2008-02-10 20:16:00 status installed linux-sound-base 1.0.14-1ubuntu2
2008-02-10 20:16:00 configure libesd-alsa0 0.2.38-0ubuntu4 0.2.38-0ubuntu4
2008-02-10 20:16:00 status unpacked libesd-alsa0 0.2.38-0ubuntu4
2008-02-10 20:16:00 status half-configured libesd-alsa0 0.2.38-0ubuntu4
2008-02-10 20:16:00 status installed libesd-alsa0 0.2.38-0ubuntu4
2008-02-10 20:16:00 trigproc libc6 2.6.1-1ubuntu10 2.6.1-1ubuntu10
2008-02-10 20:16:00 status half-configured libc6 2.6.1-1ubuntu10
2008-02-10 20:16:16 status installed libc6 2.6.1-1ubuntu10
2008-02-10 20:44:58 startup archives unpack
2008-02-10 20:45:14 upgrade amarok-xine 2:1.4.8-0ubuntu1~gutsy1 2:1.4.8-0ubuntu1~gutsy1
2008-02-10 20:45:14 status half-configured amarok-xine 2:1.4.8-0ubuntu1~gutsy1
2008-02-10 20:45:14 status unpacked amarok-xine 2:1.4.8-0ubuntu1~gutsy1
2008-02-10 20:45:14 status half-installed amarok-xine 2:1.4.8-0ubuntu1~gutsy1
2008-02-10 20:45:14 status half-installed amarok-xine 2:1.4.8-0ubuntu1~gutsy1
2008-02-10 20:45:14 status unpacked amarok-xine 2:1.4.8-0ubuntu1~gutsy1
2008-02-10 20:45:14 status unpacked amarok-xine 2:1.4.8-0ubuntu1~gutsy1
2008-02-10 20:45:15 upgrade firefox 2.0.0.11+2nobinonly-0ubuntu0.7.10 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:15 status half-configured firefox 2.0.0.11+2nobinonly-0ubuntu0.7.10
2008-02-10 20:45:15 status unpacked firefox 2.0.0.11+2nobinonly-0ubuntu0.7.10
2008-02-10 20:45:15 status half-installed firefox 2.0.0.11+2nobinonly-0ubuntu0.7.10
2008-02-10 20:45:21 status half-installed firefox 2.0.0.11+2nobinonly-0ubuntu0.7.10
2008-02-10 20:45:22 status unpacked firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:22 status unpacked firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:22 upgrade kaffeine-xine 0.8.5-0ubuntu1 0.8.5-0ubuntu1
2008-02-10 20:45:22 status half-configured kaffeine-xine 0.8.5-0ubuntu1
2008-02-10 20:45:22 status unpacked kaffeine-xine 0.8.5-0ubuntu1
2008-02-10 20:45:22 status half-installed kaffeine-xine 0.8.5-0ubuntu1
2008-02-10 20:45:23 status half-installed kaffeine-xine 0.8.5-0ubuntu1
2008-02-10 20:45:23 status unpacked kaffeine-xine 0.8.5-0ubuntu1
2008-02-10 20:45:23 status unpacked kaffeine-xine 0.8.5-0ubuntu1
2008-02-10 20:45:23 upgrade libarts1-xine 4:3.5.8-0ubuntu1 4:3.5.8-0ubuntu1
2008-02-10 20:45:23 status half-configured libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 20:45:23 status unpacked libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 20:45:23 status half-installed libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 20:45:23 status half-installed libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 20:45:24 status unpacked libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 20:45:24 status unpacked libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 20:45:24 upgrade libxine1 1.1.7-1ubuntu1 1.1.7-1ubuntu1
2008-02-10 20:45:24 status half-configured libxine1 1.1.7-1ubuntu1
2008-02-10 20:45:24 status unpacked libxine1 1.1.7-1ubuntu1
2008-02-10 20:45:24 status half-installed libxine1 1.1.7-1ubuntu1
2008-02-10 20:45:25 status half-installed libxine1 1.1.7-1ubuntu1
2008-02-10 20:45:26 status unpacked libxine1 1.1.7-1ubuntu1
2008-02-10 20:45:26 status unpacked libxine1 1.1.7-1ubuntu1
2008-02-10 20:45:26 upgrade libxine1-ffmpeg 1.1.7-1ubuntu1 1.1.7-1ubuntu1
2008-02-10 20:45:26 status half-configured libxine1-ffmpeg 1.1.7-1ubuntu1
2008-02-10 20:45:26 status unpacked libxine1-ffmpeg 1.1.7-1ubuntu1
2008-02-10 20:45:26 status half-installed libxine1-ffmpeg 1.1.7-1ubuntu1
2008-02-10 20:45:27 status half-installed libxine1-ffmpeg 1.1.7-1ubuntu1
2008-02-10 20:45:27 status unpacked libxine1-ffmpeg 1.1.7-1ubuntu1
2008-02-10 20:45:27 status unpacked libxine1-ffmpeg 1.1.7-1ubuntu1
2008-02-10 20:45:28 startup packages configure
2008-02-10 20:45:28 configure firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:28 status unpacked firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:28 status unpacked firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:28 status unpacked firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:28 status unpacked firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:28 status unpacked firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:28 status unpacked firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:28 status unpacked firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:28 status unpacked firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:28 status unpacked firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:28 status unpacked firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:28 status half-configured firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:28 status installed firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
2008-02-10 20:45:28 status triggers-pending libc6 2.6.1-1ubuntu10
2008-02-10 20:45:28 configure libxine1 1.1.7-1ubuntu1 1.1.7-1ubuntu1
2008-02-10 20:45:28 status unpacked libxine1 1.1.7-1ubuntu1
2008-02-10 20:45:28 status half-configured libxine1 1.1.7-1ubuntu1
2008-02-10 20:45:28 status installed libxine1 1.1.7-1ubuntu1
2008-02-10 20:45:28 configure libxine1-ffmpeg 1.1.7-1ubuntu1 1.1.7-1ubuntu1
2008-02-10 20:45:28 status unpacked libxine1-ffmpeg 1.1.7-1ubuntu1
2008-02-10 20:45:28 status half-configured libxine1-ffmpeg 1.1.7-1ubuntu1
2008-02-10 20:45:28 status installed libxine1-ffmpeg 1.1.7-1ubuntu1
2008-02-10 20:45:28 configure amarok-xine 2:1.4.8-0ubuntu1~gutsy1 2:1.4.8-0ubuntu1~gutsy1
2008-02-10 20:45:28 status unpacked amarok-xine 2:1.4.8-0ubuntu1~gutsy1
2008-02-10 20:45:28 status half-configured amarok-xine 2:1.4.8-0ubuntu1~gutsy1
2008-02-10 20:45:28 status installed amarok-xine 2:1.4.8-0ubuntu1~gutsy1
2008-02-10 20:45:28 configure kaffeine-xine 0.8.5-0ubuntu1 0.8.5-0ubuntu1
2008-02-10 20:45:28 status unpacked kaffeine-xine 0.8.5-0ubuntu1
2008-02-10 20:45:28 status half-configured kaffeine-xine 0.8.5-0ubuntu1
2008-02-10 20:45:28 status installed kaffeine-xine 0.8.5-0ubuntu1
2008-02-10 20:45:28 configure libarts1-xine 4:3.5.8-0ubuntu1 4:3.5.8-0ubuntu1
2008-02-10 20:45:28 status unpacked libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 20:45:28 status half-configured libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 20:45:28 status installed libarts1-xine 4:3.5.8-0ubuntu1
2008-02-10 20:45:28 trigproc libc6 2.6.1-1ubuntu10 2.6.1-1ubuntu10
2008-02-10 20:45:28 status half-configured libc6 2.6.1-1ubuntu10
2008-02-10 20:45:47 status installed libc6 2.6.1-1ubuntu10
```

Kaffeine gives me
```
00:26:41: >>> Check if another program already uses PCM <<<
00:26:41: snd_pcm_open() failed:-19:No such device
```
then if i switch it to oss rather then alsa I get
```
00:27:35: >>> Check if another program already uses PCM <<<
00:27:35: snd_pcm_open() failed:-19:No such device
00:26:50: xine: found demuxer plugin: AVI/RIFF demux plugin
00:26:50: xine: found input plugin : file input plugin
00:26:50: >>> Check if another program already uses PCM <<<
00:26:50: snd_pcm_open() failed:-19:No such device
00:26:41: >>> Check if another program already uses PCM <<<
00:26:41: snd_pcm_open() failed:-19:No such device
```

with aplay I get
```
ALSA lib confmisc.c:769:(parse_card) cannot find card _driver'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:546: audio open error: No such device
```

Lspci shows
```
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
```

If there is anything else I can give to help out figuring what the problem is let me know. I am looking for something quick to fix it... If I have to downgrade something to the previous version or something please let me know how to do that.

Any help is appreciated
Thanks Matt

---

