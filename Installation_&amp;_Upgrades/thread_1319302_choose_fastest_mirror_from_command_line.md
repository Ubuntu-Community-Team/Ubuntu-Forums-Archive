---
title: "choose fastest mirror from command line"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by pythonscript on 2009-11-08
How can I choose the fastest update mirror from the command line? I know Synaptic has this functionality, but is there a way to do this from the terminal? Thanks!

---

### Post by pythonscript on 2009-11-10
Anyone have any ideas? I'd love to add this into my update script so that ubuntu chooses the fastest mirror every time I update.

---

### Post by garvinrick4 on 2009-11-10
Here are the UK Mirrors. Take your pick.

[University Of Kent UK Mirror Service]("https://launchpad.net/ubuntu/+mirror/uk-mirror-service")                             [http]("http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/")           [ftp]("ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/")           [rsync]("rsync://rsync.mirrorservice.org/archive.ubuntu.com/ubuntu/")                  2 Gbps                             One week behind                                           [Bytemark Hosting]("https://launchpad.net/ubuntu/+mirror/bytemark-archive")                             [http]("http://mirror.bytemark.co.uk/ubuntu/")           [ftp]("ftp://mirror.bytemark.co.uk/ubuntu/")           [rsync]("rsync://mirror.bytemark.co.uk/ubuntu/")                  1 Gbps                             One day behind                                           [XILO Communications Ltd.]("https://launchpad.net/ubuntu/+mirror/mirror.as29550.net-archive")                             [http]("http://mirror.as29550.net/archive.ubuntu.com/")           [ftp]("ftp://mirror.as29550.net/archive.ubuntu.com/")                             1 Gbps                             Up to date                                           [Oxford University Computing Services]("https://launchpad.net/ubuntu/+mirror/mirror.ox.ac.uk-archive")                             [http]("http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/")           [ftp]("ftp://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/")           [rsync]("rsync://mirror.ox.ac.uk/sites/archive.ubuntu.com/")                  1 Gbps                             One week behind                                           [Goscomb Technologies Limited]("https://launchpad.net/ubuntu/+mirror/mirror.sov.uk.goscomb.net-archive")                             [http]("http://mirror.sov.uk.goscomb.net/ubuntu/")           [ftp]("ftp://mirror.sov.uk.goscomb.net/ubuntu/")                             1 Gbps                             Two days behind                                           [Ticklers.Org]("https://launchpad.net/ubuntu/+mirror/ticklers")                             [http]("http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/")           [ftp]("ftp://ftp.ticklers.org/archive.ubuntu.org/ubuntu/")           [rsync]("rsync://ftp.ticklers.org/archive.ubuntu.org/ubuntu/")                  1 Gbps                             One week behind                                           [datahop.it]("https://launchpad.net/ubuntu/+mirror/ubuntu-archives.datahop.it-archive")                             [http]("http://ubuntu-archive.datahop.it/ubuntu/")           [ftp]("ftp://ubuntu-archive.datahop.it/ubuntu/")           [rsync]("rsync://ubuntu-archive.datahop.it/ubuntu/")                  1 Gbps                             Up to date                                           [Canonical Ltd]("https://launchpad.net/ubuntu/+mirror/archive.ubuntu.com")                             [http]("http://archive.ubuntu.com/ubuntu/")           [ftp]("ftp://archive.ubuntu.com/ubuntu/")           [rsync]("rsync://archive.ubuntu.com/ubuntu/")                  100 Mbps                             Up to date                                           [The Positive Internet Company]("https://launchpad.net/ubuntu/+mirror/ubuntu.positive-internet.com-archive")                             [http]("http://ubuntu.positive-internet.com/ubuntu/")                                        100 Mbps                             Two hours behind                                           [Retrosnub Internet Services]("https://launchpad.net/ubuntu/+mirror/ubuntu.retrosnub.co.uk-archive")                             [http]("http://ubuntu.retrosnub.co.uk/ubuntu/")           [ftp]("ftp://ubuntu.retrosnub.co.uk/ubuntu/")           [rsync]("rsync://ubuntu.retrosnub.co.uk/ubuntu/")                  100 Mbps                             Six hours behind                                           [Virgin Media]("https://launchpad.net/ubuntu/+mirror/ubuntu.virginmedia.com-archive")                             [http]("http://ubuntu.virginmedia.com/archive/")           [ftp]("ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive")                             100 Mbps                             One week behind

---

### Post by pythonscript on 2009-11-11
I'm trying to find a command or set of commands I can embed in a script that will choose the fastest mirror *every time*, not just choose some arbitrary mirror from a list. Synaptic has this functionality, as shown here:

[IMG]http://img222.imageshack.us/img222/6646/bestserver.png[/IMG]

I ask about this because I also travel quite a bit, so simply picking a mirror from my home country doesn't do me much good as the fastest one, and it'd be helpful to have a script pick the fastest mirror *wherever* I am.

---

