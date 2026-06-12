---
title: "Huawei e353 Modem in Ubuntu 12.04 ( Precise )"
date: 2012-08-14
forum: Hardware
---

### Post by biggenius on 2012-08-14
I have `Huawei USB modem E353`. But it is just working with Ubuntu 12.04. I am able to connect to internet.

But I am not able to use `ixconn` and `Gammu` for retrieving messages. I need USSD Functionality. Please advice me on how can i acheive this.

Modem is detected as `Bus 002 Device 005: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM` which is not my modem.


**dsmeg**

    [   19.631536] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
    [   19.631539] Bluetooth: BNEP filters: protocol multicast
    [   19.643278] Bluetooth: RFCOMM TTY layer initialized
    [   19.643283] Bluetooth: RFCOMM socket layer initialized
    [   19.643285] Bluetooth: RFCOMM ver 1.11
    [   19.676131] type=1400 audit(1344863502.640:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=878 comm="apparmor_parser"
    [   19.683977] type=1400 audit(1344863502.648:6): apparmor="STATUS" operation="profile_load" name="/opt/extras.ubuntu.com/unity-lens-askubuntu/unity-askubuntu-daemon" pid=879 comm="apparmor_parser"
    [   19.689801] type=1400 audit(1344863502.656:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=885 comm="apparmor_parser"
    [   19.690360] type=1400 audit(1344863502.656:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=885 comm="apparmor_parser"
    [   19.692185] type=1400 audit(1344863502.656:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=882 comm="apparmor_parser"
    [   19.694865] type=1400 audit(1344863502.660:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=882 comm="apparmor_parser"
    [   19.703329] type=1400 audit(1344863502.668:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=882 comm="apparmor_parser"
    [   19.756732] ADDRCONF(NETDEV_UP): wlan0: link is not ready
    [   19.760149] ADDRCONF(NETDEV_UP): wlan0: link is not ready
    [   19.771338] jme 0000:04:00.5: irq 48 for MSI/MSI-X
    [   19.793689] jme 0000:04:00.5: eth0: Link is down
    [   19.793904] ADDRCONF(NETDEV_UP): eth0: link is not ready
    [   19.794333] ADDRCONF(NETDEV_UP): eth0: link is not ready
    [   19.935396] usb 2-1.3: USB disconnect, device number 4
    [   20.665660] init: plymouth-stop pre-start process (1228) terminated with status 1
    [   23.715659] usb 2-1.3: new high-speed USB device number 5 using ehci_hcd
    [   23.917956] scsi8 : usb-storage 2-1.3:1.5
    [   23.924254] scsi9 : usb-storage 2-1.3:1.6
    [   23.937909] usbcore: registered new interface driver usbserial
    [   23.939217] USB Serial support registered for generic
    [   23.955579] usbcore: registered new interface driver usbserial_generic
    [   23.955584] usbserial: USB Serial Driver core
    [   23.958098] USB Serial support registered for GSM modem (1-port)
    [   23.958200] option 2-1.3:1.0: GSM modem (1-port) converter detected
    [   23.958371] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB0
    [   23.958402] option 2-1.3:1.3: GSM modem (1-port) converter detected
    [   23.958515] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB1
    [   23.958531] option 2-1.3:1.4: GSM modem (1-port) converter detected
    [   23.966980] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB2
    [   23.967956] usbcore: registered new interface driver option
    [   23.967959] option: v0.7.2:USB Driver for GSM modems
    [   24.924286] scsi 8:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
    [   24.928152] scsi 9:0:0:0: Direct-Access     HUAWEI   TF CARD Storage       PQ: 0 ANSI: 2
    [   24.929646] sr1: scsi-1 drive
    [   24.930323] sr 8:0:0:0: Attached scsi CD-ROM sr1
    [   24.931510] sr 8:0:0:0: Attached scsi generic sg2 type 5
    [   24.932528] sd 9:0:0:0: Attached scsi generic sg3 type 0
    [   24.934765] sd 9:0:0:0: [sdb] Attached SCSI removable disk
    [   48.003006] PPP BSD Compression module registered
    [   48.028454] PPP Deflate Compression module registered
    [ 2409.681560] show_signal_msg: 39 callbacks suppressed
    [ 2409.681569] zenity[4231]: segfault at 32 ip 080551ad sp bf85d2c0 error 4 in zenity[8048000+14000]
    [ 2428.536619] zenity[5181]: segfault at 32 ip 080551ad sp bf8cd4e0 error 4 in zenity[8048000+14000]
    [ 2448.815826] zenity[6305]: segfault at 32 ip 080551ad sp bfd8ea20 error 4 in zenity[8048000+14000]
    [ 2461.042574] zenity[7347]: segfault at 32 ip 080551ad sp bfdda330 error 4 in zenity[8048000+14000]
    [ 2506.407263] zenity[8422]: segfault at 32 ip 080551ad sp bfc90060 error 4 in zenity[8048000+14000]

![enter image description here][1]

**Commands here** [http://pastebin.com/7pBbNNGk](http://pastebin.com/7pBbNNGk)


![enter image description here][2]


  [1]: [http://i.stack.imgur.com/mXsvQ.png](http://i.stack.imgur.com/mXsvQ.png)
  [2]: [http://i.stack.imgur.com/MLJc6.png](http://i.stack.imgur.com/MLJc6.png)

**AT Commands for E353**

    [*]H
    Manual Rejection of a Network Request for PDP Context Activation (roz&#322;&#261;czanie po&#322;&#261;czenia)
    
    [*]A
    Manual Acceptance of a Network Request for PDP Context Activation
    
    [*]D
    Mobile Originated Call to a Number (dzwonienie)
    
    [*]S0
    Ring before Automatic Answer
    
    [*]S3
    Command Line Termination Character
    
    [*]S4
    Responds Formatting Character
    
    [*]S5
    Editing Character
    
    [*]S6
    Pause before Blind Dialling
    
    [*]S7
     Wait for Completion
    
    [*]E
    Command Echo Mode
    (pl: komenda ta spowoduje wy&#347;wietlanei wszystkich oidpowiedzi modemu i naszych zapyta&#324; tj. nale&#380;y wys&#322;a&#263; komend&#281; ATE1 aby wy&#347;wietla&#322;o)
    
    [*]V
    Response Format
    
    [*]I
    Manufacturer Information about TA
    
    [*]T
    Tone Dialling
    
    [*]P
    Pulse Dialling
    
    [*]X
    CONNECT Result (mo&#380;e by&#263; przydatne przy odblokowaniu rozmów)
    
    [*]Z
    Reset to Default Configuration
    
    [*]Q
    Result Code Suppression
    
    [*]&C
    DCD-usage
    
    [*]&D
    DTR-usage (mo&#380;e by&#263; przydatne przy odblokowaniu rozmów)
    
    [*]&F
    Set all TA parameters to factory defined config
    
    [*]+CMGS
    Send Message
    
    [*]+CMGW
    Message storage
    
    [*]+CMGR
    Read a message
    
    [*]+CMGL
    Message list
    
    [*]+CMGC
    Send command
    
    [*]+CMSS
    Send Message from Storage
    
    [*]+CNMA
    New Message Acknowledge: AT+CNMA 
    Set command confirms correct reception of a new message (SMS-DELIVER or SMS-STATUS-REPORT) which is routed directly to the TE. 
    
    [*]+CSCS
    Select TE Character Set
    
    [*]+CMEE
     Report Mobile Equipment error
    Set command disables/enables the result code +CME ERROR: <err> as an indication of an error relating to the functionality of the ME
    
    [*]+CREG
    Network Registration Info
    
    [*]+CSDH
    Show Text Mode Parameters
    
    [*]+CNMI
    New message notification setting / New Message Indications to TE
    
    [*]+CGREG
    GPRS Network Registration Status / Network registration
    
    [*]+CMMS
    More Messages to Send
    
    [*]+CMGF
    Set message format / SMS Format
    
    [*]+CGSMS
    Select Service for MO SMS Messages / Message bearer domain command
    
    [*]+CSCA
    Service Centre Address / SMSC number command
    
    [*]+CSMS
    Select Message Service
    
    [*]+CSMP
    Set Text Mode Parameters (SMS)
    
    [*]+CPMS
    Message storage selection / Preferred Message Storage
    
    [*]+CMGD
    Delete Message
    
    [*]+CSCB
    Select Cell Broadcast Message Type
    
    [*]^RSTRIGGER
    ********************------brak------********************
    
    [*]+CLIP
    Calling Line Identification Presentation
    
    [*]+CLIR
    Calling Line Identification Restriction
    
    [*]+COLP
    Connected Line Identification presentation
    
    [*]+CLCC
    List Current Calls
    
    [*]+CPAS
    Phone Activity Status
    
    [*]+CSTA
    Select Type of Address
    
    [*]+CCUG
    Closed User Group
    
    [*]+CSSN
    Supplementary Service Notification
    
    [*]+CHLD
    Call Hold and Multiparty
    
    [*]+CHUP
     Hang Up Call (This command implements the same behave as ATH.)
    
    [*]+VTS
    DTMF and Tone Generation
    
    [*]^DTMF
    Command for Sending DTMF key value
    
    [*]+CRC
    Cellular Result Codes / Command for Setting the Cell Result Codes
    
    [*]+CBST
    Select Bearer Service Type / Command for Setting the Bearer Service Type 
    
    [*]+CMOD
    Call Mode (mo&#380;e by&#263; przydatne przy uaktywnianiu rozmów)
    
    [*]^ALS
    ********************------brak------********************
    
    [*]+CUUS1
    User to User Signalling Service 1 (27007-a50.pdf)
    
    [*]^CDUR
    Call Duration Query Command (EM770_AT_ Modem AT Command .pdf)
    
    [*]+CGDCONT
    Define PDP Context / PDP environment setting command / Command for Defining the PDP Context
    
    [*]+CGEQNEG
    Quality of Service Profile (Negotiated) / Command for Requesting 3G Quality of Service Profile (Negotiated)
    
    [*]+CGDSCONT
    Define Secondary PDP Context (27007-a50.pdf)
    
    [*]+CGEQREQ
     3G Quality of Service Profile (Requested) (27007-a50.pdf)
    
    [*]+CGEQMIN
    3G Quality of Service Profile (Minimum acceptable) (27007-a50.pdf)
    
    [*]+CGPADDR
    Show PDP Address / Show PDP address(es)
    
    [*]+CGCMOD
    PDP Context Modify (27007-a50.pdf)
    
    [*]+CGACT
    PDP Context Activate or Deactivate / Command for Activating or Deactivating the PDP Context
    
    [*]+CGANS
    Manual Response to a Network Request for PDP Context Activation (CTFPND-3_AT_Command_Reference.pdf) (27007-a50.pdf)
    
    [*]+CGTFT
    Traffic Flow Template Read Dynamic Parameters (27007-a50.pdf)
    
    [*]^CGDNS
    ********************------brak------********************
    
    [*]+CGAUTO
    Automatic Response to a Network Request for PDP Context Activation
    
    [*]+CGDATA
    Enter Data State
    
    [*]^TRIG
    ********************------brak------********************
    
    [*]^GCFIND
    ********************------brak------********************
    
    [*]+CGATT
    PS attach or detach / Command for Attaching the MT to or Detaching the MT from the GPRS Service
    
    [*]^CGCATT
    ********************------brak------********************
    
    [*]+COPS
    Operator Selection / PLMN selection / Command for Selecting Operators
    
    [*]+CGCLASS
    GPRS Mobile Station Class (tryby PS / CS)
    
    [*]AT+CFUN?
    Set Phone Functionality / Command for Setting the Work Mode
    
    [*]+CGMI
    Request Manufacturer Identification / Manufacturer information query command / Command for Querying the Vendor Information 
    
    [*]+CGMM
    Request Model Identification / Product model ID command / Command for Querying the Product Mode
    
    [*]+GMM
    TA Model Identification / Querying the Product Model Number Request
    
    [*]+CGMR
     Request Revision Identification / Software version number query command / Command for Querying the Software Version Number 
    
    [*]+CGSN
    Request Product Serial Number Identification / IMEI query command
    
    [*]+GSN
    Request TA serial Number / IMEI query command
    
    [*]+CIMI
    Request International Mobile Subscriber Identity / IMSI query command
    
    [*]+CSQ
    Signal Quality / RSSI query function command
    
    [*]^CBND
    "AT^CBND?" zwraca aktualne ustawienie "Band" modemu z komendy "AT^SYSCFG"
    
    [*]^CPDW
    ********************------brak------********************
    Mo&#380;e ma cos wspólnego z CPWD (g20software.pdf g20 AT Commands.book)
    
    [*]^HWVER
    Command for Querying hardware version number / Hardware version number query function
    
    [*]^HVER
    Hardware version number query function (takie smao jak ^HWVER)
    
    [*]^FHVER
    Zwraca: "Model modemu wersj&#281; firmware, wersj&#281; hardware" np. "E353s-2A 21.157.06.00.264,CH2E353SM Ver.A"
    
    [*]^PFVER
    Zwraca ci&#261;g znaków V3R i "Compile date / time"
    
    [*]+CLAC
    List All Available AT Commands
    
    [*]^SN
    Zwraca Serial number (numer seryjny urz&#261;dzenia)
    
    [*]+GCAP
    Request Overall Capabilities for TA / The Complete Capabilities List command (+GCAP) should indicate the major capability areas of the TA (27007-a50.pdf)
    
    [*]^SRVST
    Command for Indicating service state change / Service state change indication
    
    [*]^MODE
    System mode change event indication / Command for Indicating system mode change event (co&#347; nie chce dzia&#322;a&#263;, moze by&#263; przydatne do podtrzyumania HSPA+)
    
    [*]^SIMST
    SIM state change indication (co&#347; nie chce dzia&#322;a&#263;, moze by&#263; przydatne do rozpoznawania braku PS w modemie i karcie Aero2)
    
    [*]^HS
    TE-MS handshake function command / Command for Handshaking between MS and TE
    
    [*]+CPLS
    Selection of preferred PLMN list (27007-a50.pdf)
    
    [*]+CPOL
    Preferred Operator List / Preferred PLMN list
    
    [*]+CPBS
    Phonebook memory selection / Command for Selecting the Phone Book Memory
    
    [*]^CPBR
    Phonebook reading / Command for Reading the Phone Book
    
    [*]+CPBR
    Read phonebook entries / Checking the Parameter Range Supported by the +CPBR Command (HUAWEI_MU509_HSDPA_LGA_Module_AT_Command_Interface_Specification-(V100R001_01,English).pdf)
    
    [*]^CPBW
    Command for Writing the Phone Book / Phonebook writing
    
    [*]+CPBW
    Write phonebook entry / Write Phonebook Entries
    
    [*]^SCPBW
    Write Phonebook (LC6341 AT Command Set User Manual 201154154055464.pdf)
    
    [*]^SCPBR
    Read Phonebook (LC6341 AT Command Set User Manual 201154154055464.pdf)
    
    [*]+CNUM
    Subscriber Number
    
    [*]+CPBF
    Find Phonebook Entries / Command for Querying phonebook Query
    
    [*]+CSIM
     Generic SIM access (27007-a50.pdf)
    
    [*]+CPIN
    Enter PIN / PIN management command
    
    [*]^ICCID
    "AT^ICCID?" return integrated circuit card identification from the SIM card (RIM_1802G_RIM_1902G_AT_Commands_Guide.pdf)
    
    [*]^CPIN
    PIN management command ^CPIN (new feature) / Command for Manage PIN (indicate remaining password input times)
    
    [*]+CRSM
    Command for Accessing a SIM Card Through Restricted SIM Access / Restricted SIM access
    
    [*]^PNN
    EFPNN (PLMN Network Name) - contains the full and short form version of the network name 
     for the registered PLMN. 
     If the Operator Name Source is CPHS Operator Name String long and short form, 
     refer to <indValue>, the following two SIM Elementary Files are used: 
     EFONString (Operator Name String) - contains the name of the PLMN operator who issued the 
     SIM. 
     EFOPShort (Operator Name Short form) - contains a short form of the name of the PLMN 
     operator who issued the SIM. 
    (s000453c.pdf)
    ********************------brak------********************
    
    [*]^CPNN
    ********************------brak------********************
    
    [*]^OPL
    EFOPL (Operator PLMN List) - contains the PLMN identification and location ID together with 
     the index of the corresponding PNN record. 
    ********************------brak------********************
    
    [*]^CARDLOCK
    Card lock command / AT^CARDLOCK is used for unlock the datacard. When the SIM card which is not allowed by the 
    operator (Called illegal SIM card) is inserted into the datacard, the datacard can detect it is a illegal 
    SIM card and require a unlock code before it can register the network. If the right  unlock code is 
    inputted,  the  datacard  is unlocked  and  then  any  other  opertator’s  SIM  card  can  work  in  this 
    datacard. If the wrong unlock code inputted exceeds 10 times, the datacard is locked forever and 
    only  the  SIM card which  is  allowed  by  the  operator  (Called  legal  SIM card) can work with this 
    datacard. 
    
    [*]+CCWA
    Call Waiting / Command for Reporting of call waiting
    
    [*]+CCFC
    Call Forwarding Number and Conditions / Call Forwarding Command
    
    [*]+CUSD
    Unstructured Supplementary Service / USSD command
    
    [*]^CMLCK
    "AT^CMLCK=?" zwraca: "^CMLCK: ("PS")"
    ********************------brak------********************
    
    [*]+CLCK
    Facility Lock / PIN enabling and query function
    
    [*]+CPWD
    Change Password / PIN password modifying
    
    [*]^CDSF
    ********************------brak------********************
    
    [*]^CDCF
    ********************------brak------********************
    
    [*]^CDQF
    ********************------brak------********************
    
    [*]^DSFLOWCLR
    DS traffic reset
    
    [*]^DSFLOWQRY
    DS traffic query
    
    [*]^DSFLOWRPT
    DS traffic reporting
    
    [*]^CPAM
    Central Processor Auxiliary Magazine :))) / Control Plane Assurance Magazine :)))
    ********************------brak------********************
    
    [*]^TIME
    ********************------brak------********************
    
    [*]+CTZR
    Time Zone Reporting
    
    [*]^STSF
    SIM ToolKit Set Facilities (TF_PIML PLUS_AT_Commands_Interface_Guide1.pdf)
    
    [*]^STGI
    COMMAND NOT SUPPORT
    SIM ToolKit Get Information (TF_PIML PLUS_AT_Commands_Interface_Guide1.pdf)
    
    [*]^STGR
    SIM ToolKit Give Response (TF_PIML PLUS_AT_Commands_Interface_Guide1.pdf)
    
    [*]^IMSICHG
    COMMAND NOT SUPPORT
    ********************------brak------********************
    
    [*]^PDPSTUB
    ********************------brak------********************
    
    [*]^CWAS
    ********************------brak------********************
    
    [*]^CGAS
    ********************------brak------******************
    
    [*]^MFREELOCKSIZE
    "AT^MFREELOCKSIZE?" zwraca: "^MFREELOCKSIZE:liczba"
    ********************------brak------******************
    
    [*]^CPULOAD
    "AT^CPULOAD?" zwraca: "^CPULOAD:0 OK"
    ********************------brak------******************
    
    [*]^CELLINFO
    ********************------brak------******************
    
    [*]^MEANRPT
    zwraca 0
    ********************------brak------******************
    
    [*]^CCC
    ********************------brak------******************
    
    [*]^SPN
    Return (U)SIM card's  / Service Provider Name / Command for Getting service provider name
    
    [*]^CARDMODE
    Unsolicited Result Code Control (201154154055464.pdf)
    
    [*]^CURC
    Unsolicited report control command / Command for Controlling unsolicited report
    
    [*]^CMSR
    ********************------brak------******************
    
    [*]^CMGI
    ********************------brak------******************
    
    [*]^CMMT
    ********************------brak------******************
    
    [*]^AUTHDATA
    ********************------brak------******************
    
    [*]^DHCP
    (mo&#380;na sprawdza&#263; po po&#322;&#261;czeniu)
    ********************------brak------******************
    
    [*]^CRPN
    ********************------brak------******************
    
    [*]^GLASTERR
    ********************------brak------******************
    
    [*]^NDISDUP
    (&#322;&#261;czy modem w trybie NDIS)
    ********************------brak------******************
    
    [*]^NDISCONN
    ********************------brak------******************
    
    [*]^NDISSTATQRY
    (wy&#347;wietla informacje o po&#322;&#261;czneiu NDIS)
    ********************------brak------******************
    
    [*]^NDISADD
    "AT^NDISADD=?" zwraca: "^NDISADD: (0-1),(IP_Address),(Primary_DNS),(Secondary_DNS),(Primary_NBNS),(Secondary_NBNS)"
    ********************------brak------******************
    
    [*]^DNSP
    "AT^DNSP=?" zwraca "^DNSP: (-PrimaryDNS-)"
    ********************------brak------******************
    
    [*]^DNSS
    "AT^DNSS" zwraca "^DNSS: (-SecondaryDNS-)"
    ********************------brak------******************
    
    [*]^DLOADVER
    Zwraca wersj&#281; bootyloadera (oem sbl) w Download mode?
    ********************------brak------******************
    
    [*]^DLOADINFO
    Interesuj&#261;ca funkcja. Zwraca takze warto&#347;&#263; ^MODE np.:
    
    "AT^DLOADINFO?
    
    swver:21.157.06.00.264
    
    isover:UTPS21.005.11.10.264_MAC21.005.11.08.264
    
    
    webuiver:
    
    product name:E353s-2A
    
    dload type:0
    
    OK
    
    ^MODE: 5,9"
    ********************------brak------******************
    
    [*]^NVBACKUP
    All Backs up items stored in non-volatile memory
    ********************------brak------******************
    
    [*]^NVRESTORE
    zapewne przywraca backup
    ********************------brak------******************
    
    [*]^AUTHORITYVER
    zwraca wersj&#281; ?czego&#347;? (IMEI?)
    "AT^AUTHORITYVER?
    1000
    OK"
    ********************------brak------******************
    
    [*]^AUTHORITYID
    Zwraca imei i drgu&#261; liczb&#281; po precinku:
    "AT^AUTHORITYID?
    IMEI,0
    OK"
    ********************------brak------******************
    
    [*]^GODLOAD
    Prze&#322;&#261;cza w tryb Download Mode (oem sbl) b&#261;d&#378; bootloadera.
    ********************------brak------******************
    
    [*]AT^RESET
    Resetuje modem, uruchamia ponownie mo&#380;liwe, &#380;e do ustawie&#324; fabrycznych.
    ********************------brak------******************
    
    [*]^NVRSTSTTS
    ********************------brak------******************
    
    [*]^HWNATQRY
    "AT^HWNATQRY?" zwraca liczb&#281;
    ********************------brak------******************
    
    [*]^FLASHINFO
    Zwraca jakie&#347; adresy w pami&#281;ci?
    ********************------brak------******************
    
    [*]^COMM
    ********************------brak------******************
    
    [*]^HSPA
    ********************------brak------******************
    
    [*]^CSNR
    
    "AT^CSNR?" zwraca dwie liczby, analzia pochodzi z: [http://knol.google.com/k/modem-based-3g-signal-analysis#](http://knol.google.com/k/modem-based-3g-signal-analysis#)
    Range (SNR-A),(SNR-B): (-145--60),(-32-0)
    
        In response to the CSNR command, the modem responds with two numbers. Due to not knowing exactly how these numbers are measured and calculated (see Modem specifics), they have been termed SNR-A and SNR-B.
        (-145--60) means that
            SNR-A response from the modem will be a number from -145 to -60
        (-32-0) means that:
            SNR-B response from the modem will be a number from -32 to 0
    	SNR-A &#8640;SNR-A value returned from the modem
    
        Note that, unlike in the RSSI case, we defer explaining the meaning of SNR-A for later, subject to further investigation. This due to not knowing what the modem is exactly measuring in this case.
    
    SNR-B &#8640; SNR-B value returned from the modem
    
        Note that, unlike in the RSSI case, we defer explaining the meaning of SNR-B for later, subject to further investigation. This is due to not knowing what the modem is exactly measuring in this case.
    ********************------brak------******************
    
    [*]^FREQLOCK
    (kana&#322;y do blokownaia na modemie?)
    ********************------brak------******************
    
    [*]^CFPLMN
    "AT^CFPLMN?" wyswietla list&#281; operatorów do których si&#281; nie zalogoali&#347;my?
    ********************------brak------******************
    
    [*]^CQST
    przyjmuje dwie warto&#347;ci, 1 i 0
    ********************------brak------******************
    
    [*]^CAATT
    przyjmuje dwie warto&#347;ci, 1 i 0
    ********************------brak------******************
    
    [*]^SYSINFO
    zwraca sporo informacji, wyjasnienai s&#261; dost&#281;pne
    
    [*]^SYSCFG
    ustawienia, cz&#281;stotliwo&#347;ci, trybu sieci etc.
    
    [*]^RXDIV
    
    
    [*]^PCSCINFO
    
    [*]^CELLSRCH
    
    [*]+CLVL
    
    [*]^VMSET
    
    [*]^CDTMFS
    
    [*]^CDTMFE
    
    [*]+GMI
    
    [*]+GMR
    
    [*]^SETPORT
    
    [*]^VERTIME
    
    [*]^APHPLMN
    
    [*]^ANQUERY
    
    [*]^APPWRONREG
    
    [*]^APTHROUGHPUT
    
    [*]^APCONNST
    
    [*]^WIFIGLOBALMAC
    
    [*]^SCID
    
    [*]+CSQLVL
    
    [*]^CSQLVLEXT
    
    [*]^APPDMVER
    
    [*]^AUTHVER
    
    [*]^IPV6CAP
    
    [*]^DHCPV6
    
    [*]^APRAINFO
    
    [*]^APLANADDR

---

