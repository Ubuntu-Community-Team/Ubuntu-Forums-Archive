---
title: "Run Football Manager 2009 under Linux?"
date: 2008-11-23
forum: General Help
---

### Post by fedemw on 2008-11-23
Hello all,

I'm trying to run Football Manager 2009 under Wine.

I installed the application; But see what's happening.


> wine fm.exe
err:service:validate_service_config Service L"Macsvmgbbsbs" has an unknown service type
err:service:scmdatabase_load_services Invalid configuration of service L"Macsvmgbbsbs" - skipping
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Sports Interactive\\Football Manager 2009\\saAuditMD.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Sports Interactive\\Football Manager 2009\\saAuditMD.dll") not found
err:module:import_dll Library saAuditMD.dll (which is needed by L"C:\\Program Files\\Sports Interactive\\Football Manager 2009\\fm.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Sports Interactive\\Football Manager 2009\\fm.exe" failed, status c0000135



> ~/.wine/drive_c/Program Files/Sports Interactive/Football Manager 2009$ wine
Usage: wine PROGRAM [ARGUMENTS...] Run the specified program
wine --help Display this help and exit
wine --version Output version information and exit
[email]lenin@CCCP:~/.wine[/email]/drive_c/Program Files/Sports Interactive/Football Manager 2009$ wine --version
wine-1.0.1


Do you have any solution for this?

---

### Post by philinux on 2008-11-23
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14555](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14555)

---

### Post by tobias-mansson on 2008-11-24
[http://ubuntuforums.org/showthread.php?t=967618&highlight=football+manager+2009](http://ubuntuforums.org/showthread.php?t=967618&highlight=football+manager+2009)

Search before post!

---

### Post by rcayea on 2009-08-10
> **tobias-mansson said:**
> [http://ubuntuforums.org/showthread.php?t=967618&highlight=football+manager+2009](http://ubuntuforums.org/showthread.php?t=967618&highlight=football+manager+2009)

Search before post!

Either reply nicely or don't reply. He appears to be trying to install the full version and that is a tough thing to do with the link you provided - that link works well with demo, but not full version!

---

