---
title: "[SOLVED] Banshee 1.2.1 stops importing"
date: 2008-09-01
forum: General Help
---

### Post by petzworld999 on 2008-09-01
Hello everybody. I am trying to import my huge music collection into Banshee, but it always stops importing at 34%, when the error message count is 140. Does anyone have any idea on what is going on and how to fix it? My logfile is this:

```


[Info  08:39:54.137] Running Banshee 1.2.1
[Info  08:39:55.482] All services are started 1.235896s
[Info  08:39:56.090] nereid Client Started
Error in avahi-sharp event loop: System.IndexOutOfRangeException: Array index is out of range.
at Mono.Zeroconf.Providers.Avahi.TxtRecord..ctor (byte[][]) <0x001ab>
at Mono.Zeroconf.Providers.Avahi.Service.get_TxtRecord () <0x0001c>
at Daap.ServiceLocator.OnServiceResolved (object,Mono.Zeroconf.ServiceResolvedEventArgs) <0x0013f>
at Mono.Zeroconf.Providers.Avahi.ResolvableService.OnServiceResolved (object,Avahi.ServiceInfoArgs) <0x00095>
at Avahi.ServiceResolver.OnServiceResolverCallback (intptr,int,Avahi.Protocol,Avahi.ResolverEvent,intptr,intptr,intptr,intptr,intptr,uint16,intptr,Avahi.LookupResultFlags,intptr) <0x00279>
at (wrapper native-to-managed) Avahi.ServiceResolver.OnServiceResolverCallback (intptr,int,Avahi.Protocol,Avahi.ResolverEvent,intptr,intptr,intptr,intptr,intptr,uint16,intptr,Avahi.LookupResultFlags,intptr) <0x00069>
at (wrapper managed-to-native) Avahi.Client.avahi_simple_poll_loop (intptr) <0x00004>
at Avahi.Client.PollLoop () <0x00029>

[Warn  08:40:51.172] Caught an exception - No such file or directory [ENOENT]. (in `')


```

---

### Post by dustigroove on 2008-09-07
[COLOR=Red]* Correction - see post below.[/COLOR]

Unfortunately I don't have a solution, but can confirm that this appears to be a bug in v1.2.1 of Banshee as it occurs for me as well. It seems to be related to Banshee choking on the file name or metadata for the music files when importing. I noted which artists it would stop on and then removed non-alphanumeric characters from the name and that appeared to do the trick for most all instances where it froze up during import.

Unfortunately there are still a few artists/files that seem to choke the process no matter what I do... going back to Amarok for now as this is a bit of a deal breaker.

Cheers

---

### Post by dustigroove on 2008-09-09
A small correction to my previous post. It appears that it was not the file name but the fact that some of these files had album art embedded in their ID3 tags. When I used EasyTAG to batch rename the files, I inadvertently changed the tag version as well which allowed the files to then be imported.

See the related bug [here]("http://bugzilla.gnome.org/show_bug.cgi?id=533689"):
[http://bugzilla.gnome.org/show_bug.cgi?id=533689](http://bugzilla.gnome.org/show_bug.cgi?id=533689)

Cheers

---

### Post by petzworld999 on 2008-09-09
Well. There it is. My problem is solved. Thank you very much.

---

