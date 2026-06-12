---
title: "[SOLVED] updates not working"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by roshanjose on 2008-12-15
this is what i get when i try apt-get update


cplab2-59@cplab2-59:~$ sudo apt-get update
Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
  Could not resolve 'archive.canonical.com'
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_IN
  Could not resolve 'archive.canonical.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release.gpg
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-security Release.gpg
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release.gpg
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_IN
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_IN
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_IN
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_IN
  Could not resolve 'security.ubuntu.com'
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_IN
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_IN
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_IN
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_IN
  Could not resolve 'packages.medibuntu.org'
Reading package lists... Done             
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_IN.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/Release.gpg](http://packages.medibuntu.org/dists/hardy/Release.gpg)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/i18n/Translation-en_IN.bz2](http://packages.medibuntu.org/dists/hardy/free/i18n/Translation-en_IN.bz2)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_IN.bz2](http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_IN.bz2)  Could not resolve 'packages.medibuntu.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by ikonia on 2008-12-15
from the look of this I'd say your dns service is not responding.

try nslookup or dig to test it with other urls/sites

---

### Post by roshanjose on 2008-12-15
well the problem was with the dns...i didnt set it up....thank you

---

### Post by dr_smit on 2009-01-28
please elaborate what was the problem and what and how it was solved as I also face something similar:

apt-get update
W: Failed to fetch [http://packages.medibuntu.org/dists/intrepid/Release.gpg](http://packages.medibuntu.org/dists/intrepid/Release.gpg)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/intrepid/free/i18n/Translation-en_IN.bz2](http://packages.medibuntu.org/dists/intrepid/free/i18n/Translation-en_IN.bz2)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/intrepid/non-free/i18n/Translation-en_IN.bz2](http://packages.medibuntu.org/dists/intrepid/non-free/i18n/Translation-en_IN.bz2)  Could not resolve 'packages.medibuntu.org'

---

### Post by roshanjose on 2009-01-29
check whether your internet is working.

type  network-admin restart   in terminal


and click unlock and type in your password and check for the ip address and also check in the DNS address.

The DNS address will be provided by your Internet Provider.

Now go to the terminal and type ping <your DNS address>    (without the <> symbol)

And see whether it is able to send the packets

---

### Post by harsh1kumar on 2009-09-09
Hey all, 

I am using Kubuntu 9.10 alpha 5. I get the same errors. My internet is working. I also tried to ping my dns servers and its working. But apt-get is not working.I am not able to install softwares from PackageKit GUI also as it also doesn't seems to connect to internet. I am behind a proxy server. So I also tried after entering this:

http_proxy=http://proxy:port


but still i got same error.

---

### Post by nicomagliaro on 2009-09-09
[B]hi everybody
its  my firts time at the forum... so this s the issue
i am running kubuntu jaunty and when a update ther s a problem with some repository
[/B]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                                                                                                           
  404 Not Found                                                                                                                                             
Descargados 8624B en 15s (543B/s)                                                                                                                           
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 60D11217247D1CFF                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2ED6BB6042C24D89                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 3F2A5EE4B796B6FE                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 61270A939E324B12                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 08829DF6676AB6B9                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 7889D725DA6DEEAA                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 0B47F0A6B88A1AA8                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 3CCBDA4000FD2D7B                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 0F7482EBF3004382                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 19C98318F87FE1BD                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY F586F9AD744BF4D0                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY C9F2BA9509399DB5                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 4B1E287796DD5C9A                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY ED649F97DE6BFD99                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2A8E3034D018A4CE                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY D90C3C3D0A3A05EF                                                                                                                                            
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY7D0AC3554929B943
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY56F10C25685D166A
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY727D031129047922
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY61DD528B1D9D38E5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEYD0AFF96872D340A3
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY9761EDC37AB674BA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY6321D230F17465B8
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY434FC649FF25E89C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY5A9BF3BB4E5E17B5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY13551B881504888C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY0E23917F5D9DCE6C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEYFC6D7D9D009ED615
W: Imposible obtener [http://ppa.launchpad.net/ted-gould/ubuntu/dists/jaunty/main/binary-amd64/Packages](http://ppa.launchpad.net/ted-gould/ubuntu/dists/jaunty/main/binary-amd64/Packages)  404 Not Found
[B]
how can i fix it
thanx
[/B]

---

