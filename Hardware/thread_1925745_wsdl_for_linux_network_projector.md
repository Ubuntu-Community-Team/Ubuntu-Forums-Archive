---
title: "wsdl for linux network projector"
date: 2012-02-15
forum: Hardware
---

### Post by 100GodinaSamoce on 2012-02-15
[FONT=Segoe UI]Dear all,[/FONT]
 
[FONT=Segoe UI]I have a favor to ask. I’ve searched the entire internet trying to find WSDL for network projector without any success. Can anyone provide me information, which operations are required to be exposed as a part of service interface (are names relevant here?), in order to device be recognized by Windows 7 Connect to Network Projector Wizard? Is that crucial in discovery process – I assume if device only advertises itself as a projector (by its type), and not satisfied the required functionality, it will not be listed as a network projector?[/FONT]
 
[FONT=Segoe UI]I want to emphasize that I’m using ws4d-gsoap toolkit.[/FONT]
 

[FONT=Segoe UI]I can only assume that service needs to implement:[/FONT]
[LIST]
[*][FONT=Segoe UI]Connect (connect to endpoint device – target service: opening the RDP protocol)/Disconnect[/FONT]
[*][FONT=Segoe UI]GetDisplaySettings/SetDisplaySettings (resolution, brightness, etc.)[/FONT]
[*][FONT=Segoe UI]CheckPassword (authorization )[/FONT]
[*][FONT=Segoe UI]GetState etc.[/FONT]
[/LIST][FONT=Segoe UI]Thanks in advance,[/FONT]
[FONT=Segoe UI]Damir[/FONT]

---

