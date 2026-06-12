---
title: "Jaunty servers weird"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Roanoke on 2009-04-25
I can't access the jaunty servers when doing apt-get update. Here's the log:
```

Hit http://archive.canonical.com jaunty Release.gpg
Ign http://archive.canonical.com jaunty/partner Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Get:1 http://ppa.launchpad.net jaunty Release.gpg [307B]
Hit http://packages.medibuntu.org jaunty Release.gpg
Ign http://packages.medibuntu.org jaunty/free Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Hit http://archive.canonical.com jaunty Release
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Get:2 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Ign http://ppa.launchpad.net gutsy Release.gpg
Ign http://ppa.launchpad.net gutsy/main Translation-en_US
Get:3 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Get:4 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US
Hit http://packages.medibuntu.org jaunty Release
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty-backports Release.gpg
Ign http://us.archive.ubuntu.com jaunty-backports/main Translation-en_US
Ign http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Get:5 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Get:6 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Ign http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Get:7 http://ppa.launchpad.net jaunty Release [31.1kB]
Ign http://archive.canonical.com jaunty/partner Packages
Hit http://security.ubuntu.com jaunty-security/main Packages
Ign http://us.archive.ubuntu.com jaunty-backports/restricted Translation-en_US
Hit http://packages.medibuntu.org jaunty/free Packages
Get:8 http://ppa.launchpad.net jaunty Release [52.9kB]
Get:9 http://ppa.launchpad.net jaunty Release [31.1kB]
Get:10 http://ppa.launchpad.net gutsy Release [27.6kB]
Get:11 http://ppa.launchpad.net jaunty Release [52.9kB]
Ign http://archive.canonical.com jaunty/partner Sources
Get:12 http://ppa.launchpad.net jaunty Release [52.9kB]
Ign http://ppa.launchpad.net jaunty Release
Get:13 http://ppa.launchpad.net jaunty Release [52.9kB]
Get:14 http://ppa.launchpad.net jaunty Release [52.9kB]
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Ign http://ppa.launchpad.net jaunty Release
Ign http://ppa.launchpad.net jaunty Release
Ign http://ppa.launchpad.net jaunty Release
Ign http://ppa.launchpad.net jaunty Release
Ign http://ppa.launchpad.net jaunty Release
Ign http://ppa.launchpad.net jaunty Release
Ign http://us.archive.ubuntu.com jaunty-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release
Hit http://us.archive.ubuntu.com jaunty-updates Release
Hit http://us.archive.ubuntu.com jaunty-backports Release
Hit http://packages.medibuntu.org jaunty/non-free Packages
Ign http://ppa.launchpad.net jaunty Release
Hit http://archive.canonical.com jaunty/partner Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Sources
Ign http://ppa.launchpad.net gutsy/main Packages
Ign http://ppa.launchpad.net gutsy/main Sources
Ign http://ppa.launchpad.net jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Sources
Hit http://archive.canonical.com jaunty/partner Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Ign http://ppa.launchpad.net jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Sources
Ign http://ppa.launchpad.net jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Sources
Ign http://ppa.launchpad.net jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Ign http://ppa.launchpad.net jaunty/main Sources
Ign http://ppa.launchpad.net jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Sources
Ign http://ppa.launchpad.net jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Sources
Ign http://ppa.launchpad.net jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-backports/main Packages
Hit http://us.archive.ubuntu.com jaunty-backports/restricted Packages
Ign http://ppa.launchpad.net jaunty/main Sources
Ign http://ppa.launchpad.net jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net gutsy/main Packages
Hit http://ppa.launchpad.net gutsy/main Sources
Ign http://ppa.launchpad.net jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty-backports/universe Packages
Hit http://us.archive.ubuntu.com jaunty-backports/multiverse Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Ign http://ppa.launchpad.net jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Sources
Err http://ppa.launchpad.net jaunty/main Packages
  404 Not Found
Err http://ppa.launchpad.net jaunty/main Sources
  404 Not Found
Err http://ppa.launchpad.net jaunty/main Packages
  404 Not Found
Err http://ppa.launchpad.net jaunty/main Sources
  404 Not Found
Hit http://archive.ubuntu.com jaunty Release.gpg
Ign http://archive.ubuntu.com jaunty/main Translation-en_US
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://archive.ubuntu.com jaunty Release
Hit http://archive.ubuntu.com jaunty/main Sources
Hit http://archive.ubuntu.com jaunty/restricted Sources
Hit http://archive.ubuntu.com jaunty/main Packages
Hit http://archive.ubuntu.com jaunty/universe Packages
Hit http://archive.ubuntu.com jaunty/restricted Packages
Hit http://archive.ubuntu.com jaunty/multiverse Packages
Fetched 1850B in 13s (139B/s)

```

---

### Post by Roanoke on 2009-04-25
Nevermind, this was my own stupidity (those were custom ppas)

---

