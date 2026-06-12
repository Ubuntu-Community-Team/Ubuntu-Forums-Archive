---
title: "Toshiba A-500 Satellite CD drive problem"
date: 2011-02-09
forum: Hardware
---

### Post by djonko on 2011-02-09
Hello,

I have a Toshiba SA-50-522 (A-500 series) and this laptop has horrible problems with the I855 intel bug, so I decided to revert back to windows XP for the time being.

Now my cd drive isn't working properly. First it said that all the cd's that I inserted were blank. Audio, Data, everything was blank.

So I tried burning a cd with brasero to see if that works. That worked, I burned the cd.

But now, everytime I insert a cd into the drive, the drive disappears.

Can anyone help me with this?

Thanks

EDIT:
When I type Dmesg in terminal I get this;

77.724004] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
[   77.724031] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
[   77.724041] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
[   77.724051] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
[   80.607031] lib80211_crypt: registered algorithm 'WEP'
[  266.394635] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.394644] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.394651] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.394659] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.394672] end_request: I/O error, dev sr0, sector 0
[  266.394679] Buffer I/O error on device sr0, logical block 0
[  266.397981] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.397987] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.397993] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.398000] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.398011] end_request: I/O error, dev sr0, sector 0
[  266.398015] Buffer I/O error on device sr0, logical block 0
[  266.401284] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.401291] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.401298] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.401305] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.401316] end_request: I/O error, dev sr0, sector 0
[  266.401320] Buffer I/O error on device sr0, logical block 0
[  266.404692] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.404699] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.404705] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.404713] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.404724] end_request: I/O error, dev sr0, sector 0
[  266.404729] Buffer I/O error on device sr0, logical block 0
[  266.409547] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.409557] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.409564] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.409572] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.409585] end_request: I/O error, dev sr0, sector 0
[  266.409593] Buffer I/O error on device sr0, logical block 0
[  266.412922] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.412929] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.412936] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.412943] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.412955] end_request: I/O error, dev sr0, sector 0
[  266.412961] Buffer I/O error on device sr0, logical block 0
[  266.416298] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.416304] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.416310] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.416317] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.416328] end_request: I/O error, dev sr0, sector 0
[  266.416332] Buffer I/O error on device sr0, logical block 0
[  266.419589] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.419595] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.419601] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.419608] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.419620] end_request: I/O error, dev sr0, sector 0
[  266.419624] Buffer I/O error on device sr0, logical block 0
[  266.423032] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.423039] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.423046] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.423053] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.423065] end_request: I/O error, dev sr0, sector 0
[  266.423071] Buffer I/O error on device sr0, logical block 0
[  266.427525] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.427534] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.427541] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.427548] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.427561] end_request: I/O error, dev sr0, sector 0
[  266.427567] Buffer I/O error on device sr0, logical block 0
[  266.430869] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.430876] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.430883] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.430890] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.430902] end_request: I/O error, dev sr0, sector 0
[  266.434185] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.434192] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.434199] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.434206] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.434217] end_request: I/O error, dev sr0, sector 0
[  266.437539] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.437546] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.437552] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.437559] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.437571] end_request: I/O error, dev sr0, sector 0
[  266.440848] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.440856] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.440862] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.440869] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.440880] end_request: I/O error, dev sr0, sector 0
[  266.444172] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.444179] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.444185] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.444192] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.444203] end_request: I/O error, dev sr0, sector 0
[  266.447525] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.447532] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.447538] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.447546] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.447557] end_request: I/O error, dev sr0, sector 0
[  266.453230] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.453239] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.453247] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.453255] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.453267] end_request: I/O error, dev sr0, sector 0
[  266.456650] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.456658] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.456664] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.456671] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.456683] end_request: I/O error, dev sr0, sector 0
[  266.459987] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.459997] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.460042] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.460051] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.460063] end_request: I/O error, dev sr0, sector 0
[  266.466612] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.466622] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.466629] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.466637] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.466650] end_request: I/O error, dev sr0, sector 0
[  266.470033] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.470041] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.470048] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.470056] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.470068] end_request: I/O error, dev sr0, sector 0
[  266.473365] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.473371] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.473378] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.473385] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.473396] end_request: I/O error, dev sr0, sector 0
[  266.476730] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.476738] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.476745] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.476752] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.476764] end_request: I/O error, dev sr0, sector 0
[  266.480186] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.480193] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.480199] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.480207] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.480219] end_request: I/O error, dev sr0, sector 0
[  266.483545] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.483553] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.483559] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.483567] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.483579] end_request: I/O error, dev sr0, sector 0
[  266.486981] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.486989] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.486995] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.487003] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.487015] end_request: I/O error, dev sr0, sector 0
[  266.490316] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.490324] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.490331] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.490339] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.490351] end_request: I/O error, dev sr0, sector 0
[  266.493646] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.493652] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.493658] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.493665] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.493677] end_request: I/O error, dev sr0, sector 0
[  266.496995] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.497003] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.497009] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.497017] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.497029] end_request: I/O error, dev sr0, sector 0
[  266.500352] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.500359] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.500365] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.500373] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.500384] end_request: I/O error, dev sr0, sector 0
[  266.507616] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.507625] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.507631] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.507639] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.507652] end_request: I/O error, dev sr0, sector 0
[  266.510960] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.510967] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.510973] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.510980] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.510992] end_request: I/O error, dev sr0, sector 0
[  266.514267] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.514274] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.514280] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.514288] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.514299] end_request: I/O error, dev sr0, sector 0
[  266.518184] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.518191] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.518197] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.518205] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.518216] end_request: I/O error, dev sr0, sector 0
[  266.521492] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.521499] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.521506] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.521513] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.521524] end_request: I/O error, dev sr0, sector 0
[  266.524797] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.524804] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.524810] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.524816] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.524828] end_request: I/O error, dev sr0, sector 0
[  266.528109] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.528115] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.528121] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.528128] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.528139] end_request: I/O error, dev sr0, sector 0
[  266.531407] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.531414] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.531420] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.531427] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.531438] end_request: I/O error, dev sr0, sector 0
[  266.534709] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.534716] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.534722] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.534729] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.534740] end_request: I/O error, dev sr0, sector 0
[  266.540667] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.540674] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.540681] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.540688] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.540700] end_request: I/O error, dev sr0, sector 0
[ 5342.387206] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.387216] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.387224] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.387232] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.387244] end_request: I/O error, dev sr0, sector 0
[ 5342.387252] quiet_error: 30 callbacks suppressed
[ 5342.387256] Buffer I/O error on device sr0, logical block 0
[ 5342.391041] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.391051] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.391057] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.391065] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.391077] end_request: I/O error, dev sr0, sector 0
[ 5342.391084] Buffer I/O error on device sr0, logical block 0
[ 5342.398224] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.398232] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.398240] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.398248] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.398260] end_request: I/O error, dev sr0, sector 0
[ 5342.398268] Buffer I/O error on device sr0, logical block 0
[ 5342.401592] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.401598] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.401605] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.401612] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.401624] end_request: I/O error, dev sr0, sector 0
[ 5342.401629] Buffer I/O error on device sr0, logical block 0
[ 5342.404962] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.404971] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.404977] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.404985] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.404997] end_request: I/O error, dev sr0, sector 0
[ 5342.405004] Buffer I/O error on device sr0, logical block 0
[ 5342.408638] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.408648] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.408655] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.408663] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.408675] end_request: I/O error, dev sr0, sector 0
[ 5342.408682] Buffer I/O error on device sr0, logical block 0
[ 5342.411974] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.411982] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.411988] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.411996] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.412079] end_request: I/O error, dev sr0, sector 0
[ 5342.412085] Buffer I/O error on device sr0, logical block 0
[ 5342.415442] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.415450] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.415457] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.415464] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.415476] end_request: I/O error, dev sr0, sector 0
[ 5342.415482] Buffer I/O error on device sr0, logical block 0
[ 5342.418788] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.418796] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.418803] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.418810] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.418821] end_request: I/O error, dev sr0, sector 0
[ 5342.418826] Buffer I/O error on device sr0, logical block 0
[ 5342.422105] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.422113] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.422119] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.422127] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.422139] end_request: I/O error, dev sr0, sector 0
[ 5342.422145] Buffer I/O error on device sr0, logical block 0
[ 5342.425478] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.425486] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.425492] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.425499] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.425511] end_request: I/O error, dev sr0, sector 0
[ 5342.428804] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.428811] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.428817] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.428824] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.428836] end_request: I/O error, dev sr0, sector 0
[ 5342.432119] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.432126] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.432132] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.432139] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.432150] end_request: I/O error, dev sr0, sector 0
[ 5342.435469] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.435476] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.435483] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.435491] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.435502] end_request: I/O error, dev sr0, sector 0
[ 5342.438786] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.438792] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.438799] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.438806] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.438818] end_request: I/O error, dev sr0, sector 0
[ 5342.442090] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.442097] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.442103] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.442110] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.442121] end_request: I/O error, dev sr0, sector 0
[ 5342.445430] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.445436] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.445442] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.445449] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.445460] end_request: I/O error, dev sr0, sector 0
[ 5342.448725] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.448731] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.448738] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.448745] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.448757] end_request: I/O error, dev sr0, sector 0
[ 5342.452053] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.452060] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.452066] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.452073] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.452085] end_request: I/O error, dev sr0, sector 0
[ 5342.455651] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.455659] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.455665] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.455673] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.455684] end_request: I/O error, dev sr0, sector 0
[ 5342.458953] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.458959] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.458965] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.458972] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.458983] end_request: I/O error, dev sr0, sector 0
[ 5342.462245] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.462251] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.462257] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.462263] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.462275] end_request: I/O error, dev sr0, sector 0
[ 5342.465588] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.465595] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.465601] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.465607] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.465619] end_request: I/O error, dev sr0, sector 0
[ 5342.468885] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.468892] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.468898] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.468906] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.468917] end_request: I/O error, dev sr0, sector 0
[ 5342.472184] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.472190] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.472196] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.472203] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.472215] end_request: I/O error, dev sr0, sector 0
[ 5342.475523] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.475530] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.475536] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.475543] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.475555] end_request: I/O error, dev sr0, sector 0
[ 5342.478823] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.478829] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.478835] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.478842] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.478854] end_request: I/O error, dev sr0, sector 0
[ 5342.482116] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.482122] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.482128] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.482135] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.482146] end_request: I/O error, dev sr0, sector 0
[ 5342.485710] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.485717] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.485724] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.485731] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.485742] end_request: I/O error, dev sr0, sector 0
[ 5342.489267] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.489276] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.489283] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.489291] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.489304] end_request: I/O error, dev sr0, sector 0
[ 5342.492608] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.492614] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.492620] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.492627] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.492639] end_request: I/O error, dev sr0, sector 0
[ 5342.496541] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.496551] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.496558] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.496566] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.496578] end_request: I/O error, dev sr0, sector 0
[ 5342.499906] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.499913] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.499919] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.499927] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.499939] end_request: I/O error, dev sr0, sector 0
[ 5342.503274] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.503280] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.503287] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.503294] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.503305] end_request: I/O error, dev sr0, sector 0
[ 5342.506620] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.506628] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.506634] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.506641] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.506653] end_request: I/O error, dev sr0, sector 0
[ 5342.509984] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.509990] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.509996] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.510003] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.510015] end_request: I/O error, dev sr0, sector 0
[ 5342.514258] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.514266] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.514272] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.514280] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.514292] end_request: I/O error, dev sr0, sector 0
[ 5342.517596] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.517603] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.517610] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.517617] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.517629] end_request: I/O error, dev sr0, sector 0
[ 5342.520931] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.520937] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.520943] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.520950] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.520962] end_request: I/O error, dev sr0, sector 0
[ 5342.524276] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5342.524283] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 5342.524289] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[ 5342.524296] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 5342.524307] end_request: I/O error, dev sr0, sector 0

---

