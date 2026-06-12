---
title: "MonoDevelop/Root Issue"
date: 2005-11-25
forum: General Help
---

### Post by Othersider on 2005-11-25
I installed mono from the installer provided on their site.  Installation goes well, but it won't run when executed normally:
```

me@localhost:/opt/mono-1.1.10/bin$ sudo ./monodevelop
System.TypeInitializationException: An exception was thrown by the type initializer for Gnome.ModuleInfo ---> System.DllNotFoundException: gnomesharpglue-2
in (wrapper managed-to-native) Gnome.ModuleInfo:gnomesharp_gnome_moduleinfo_get_name_offset ()
in <0x00008> Gnome.ModuleInfo:.cctor ()--- End of inner exception stack trace ---

in <0x00000> <unknown method>
in <0x00025> Gnome.Modules:get_UI ()
in <0x00440> MonoDevelop.Ide.Gui.IdeStartup:Run (System.String[] args)
in <0x00169> MonoDevelop.Core.AddIns.AddInService:StartApplication (System.String addinId, System.String[] parameters)

```

MonoDevelop opens and runs perfectly, however, if I gain full superuser permissions:
```

me@localhost:/opt/mono-1.1.10/bin$ su
Password:
root@localhost:/opt/mono-1.1.10/bin# ./monodevelop

``` 
This becomes a problem because I can't launch it directly from any shortcuts or icons.  Any ideas?

---

### Post by CapnCook on 2005-12-03
Did you ever figure this out? I am having the same problem, except I don't have to have su privilages. I can just run ./monodevelop in a regular terminal window.

---

### Post by teaker1s on 2005-12-03
run with gksudo or sudo su

failing that it could be installed with 'fakeroot' download from synaptic

---

