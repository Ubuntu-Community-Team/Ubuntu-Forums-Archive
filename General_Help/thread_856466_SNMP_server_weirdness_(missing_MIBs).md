---
title: "SNMP server weirdness (missing MIBs?)"
date: 2008-07-11
forum: General Help
---

### Post by Inwards on 2008-07-11
This issue is driving me mad. It looks like I'm missing MIB modules or something. They all seem to be present in the /usr/share/snmp/mibs folder, but every tool I try doesn't display any data at all. Here's what I get from snmpwalk:

inwards@machinder:/usr/share/snmp/mibs$ snmpwalk -v1 -c public localhost
SNMPv2-MIB::sysDescr.0 = STRING: Linux machinder 2.6.24-19-server #1 SMP Wed Jun 18 14:44:47 UTC 2008 x86_64
SNMPv2-MIB::sysObjectID.0 = OID: NET-SNMP-MIB::netSnmpAgentOIDs.10
DISMAN-EVENT-MIB::sysUpTimeInstance = Timeticks: (42545) 0:07:05.45
SNMPv2-MIB::sysContact.0 = STRING: Inwards
SNMPv2-MIB::sysName.0 = STRING: machinder
SNMPv2-MIB::sysLocation.0 = STRING: Terminus
SNMPv2-MIB::sysORLastChange.0 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORID.1 = OID: SNMP-FRAMEWORK-MIB::snmpFrameworkMIBCompliance
SNMPv2-MIB::sysORID.2 = OID: SNMP-MPD-MIB::snmpMPDCompliance
SNMPv2-MIB::sysORID.3 = OID: SNMP-USER-BASED-SM-MIB::usmMIBCompliance
SNMPv2-MIB::sysORID.4 = OID: SNMPv2-MIB::snmpMIB
SNMPv2-MIB::sysORID.5 = OID: TCP-MIB::tcpMIB
SNMPv2-MIB::sysORID.6 = OID: IP-MIB::ip
SNMPv2-MIB::sysORID.7 = OID: UDP-MIB::udpMIB
SNMPv2-MIB::sysORID.8 = OID: SNMP-VIEW-BASED-ACM-MIB::vacmBasicGroup
SNMPv2-MIB::sysORDescr.1 = STRING: The SNMP Management Architecture MIB.
SNMPv2-MIB::sysORDescr.2 = STRING: The MIB for Message Processing and Dispatching.
SNMPv2-MIB::sysORDescr.3 = STRING: The management information definitions for the SNMP User-based Security Model.
SNMPv2-MIB::sysORDescr.4 = STRING: The MIB module for SNMPv2 entities
SNMPv2-MIB::sysORDescr.5 = STRING: The MIB module for managing TCP implementations
SNMPv2-MIB::sysORDescr.6 = STRING: The MIB module for managing IP and ICMP implementations
SNMPv2-MIB::sysORDescr.7 = STRING: The MIB module for managing UDP implementations
SNMPv2-MIB::sysORDescr.8 = STRING: View-based Access Control Model for SNMP.
SNMPv2-MIB::sysORUpTime.1 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.2 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.3 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.4 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.5 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.6 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.7 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.8 = Timeticks: (0) 0:00:00.00
End of MIB

If I try to query any of the MIBs I get something like:

inwards@machinder:/usr/share/snmp/mibs$ sudo snmpwalk -v2c -c public localhost ip
IP-MIB::ip = No more variables left in this MIB View (It is past the end of the MIB tree)

---

### Post by freddez on 2010-04-26
Put that lines on top of snmpd.conf

rocommunity public 127.0.0.1
rocommunity public <your client host>

---

