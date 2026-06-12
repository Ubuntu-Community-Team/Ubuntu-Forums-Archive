---
title: "Trouble installing Logitech G110 keyboard"
date: 2011-03-03
forum: Hardware
---

### Post by Wolfcry on 2011-03-03
I'm trying to get my keaboard to work, but g15daemon refuses to work. 
I get the following error-message during installation:

$ sudo apt-get install g15daemon
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Leser tilstandsinformasjon ... Ferdig   
Følgende NYE pakker vil bli installert:
  g15daemon
0 oppgraderte, 1 nylig installerte, 0 å fjerne og 0 ikke oppgradert.
Må hente 0B/36,7kB med arkiver.
Etter denne operasjonen vil 246kB ekstra diskplass bli brukt.
Velger den tidligere fravalgte pakken g15daemon.
(Leser database ... 164559 filer og kataloger er installerte.)
Pakker ut g15daemon (fra .../g15daemon_1.9.5.3-8ubuntu1_amd64.deb) ...
Behandler utløsere for man-db ...
Behandler utløsere for ureadahead ...
Setter opp g15daemon (1.9.5.3-8ubuntu1) ...
Starting g15daemon: .../dev/input/uinput not found ...invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: Feil ved behandling av g15daemon (--configure):
 underprosessen installerte post-installation skript returnerte feilstatus 1
Det oppsto feil ved behandling av:
 g15daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

(language is norwegian)

I've used google to find a solution, but can't find anything. Is there a solution to this problem?

Running Ubuntu 10.04

---

