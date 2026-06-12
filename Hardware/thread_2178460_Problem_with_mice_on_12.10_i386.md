---
title: "Problem with mice on 12.10 i386"
date: 2013-10-03
forum: Hardware
---

### Post by RaZoR1394 on 2013-10-03
Hi.

I've been running 12.10 on this lowbudget HP laptop for some months and lately there have been problems with mice. After the computer boots up with any mice connected the mouse works a few minutes then it gets slower and locks up. There are loads of error in the system log. There have not been any updates to the system prior to these errors. I have never seen this error like this before. If I disconnect and reconnect the mouse it goes through the same process again (errrors, slow, lockup).

#dmesg

> [ 1200.801994] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1200.825756] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1200.849622] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1200.865718] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1200.881688] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1200.961526] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1300.412215] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1300.428148] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1300.460249] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1300.483937] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1300.499902] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1307.821494] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1307.845327] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1460.837836] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1460.861659] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1460.877774] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1460.909744] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1460.957716] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.542432] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.572547] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.604333] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.628437] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.660323] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.684155] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.716213] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.740195] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.772103] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.788071] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.812044] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.843957] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.867938] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.899853] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.947632] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1469.979766] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1470.067391] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1470.083484] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1470.099476] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1470.131475] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1470.155340] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1470.181079] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1479.220992] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1486.530850] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1486.570839] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1486.618673] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1486.658662] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1486.706501] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1486.738459] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1486.762593] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1486.794323] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1497.576435] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1503.652519] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1503.728771] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1503.760692] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1503.776637] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1503.792588] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1503.842860] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1503.864592] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1503.896386] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1503.920173] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1503.992072] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.016176] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.048086] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.072174] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.095990] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.120109] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.135909] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.151890] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.183815] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.239701] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.255683] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.287609] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.320307] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.614962] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.654917] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.678864] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.718720] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.734976] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.750746] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.767544] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.790785] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.814689] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.830559] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.846501] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.870488] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.895299] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.910364] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.934244] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.966264] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.982255] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1504.998126] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1505.022178] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1505.046105] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1505.094003] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1505.120325] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1505.149904] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1505.174731] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1505.197957] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1505.221762] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1505.760195] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1513.301739] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1513.341645] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1513.373605] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1513.405474] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1513.445439] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1513.470256] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1513.485274] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1513.501338] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1513.525152] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1514.159548] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1517.000131] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1517.014482] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1517.030348] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1517.078227] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1517.094639] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1517.110189] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1517.142115] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1517.158063] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1517.221944] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1521.504990] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1524.754498] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1525.701090] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1525.725936] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1525.749264] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1525.796852] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1525.828915] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1525.844998] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1525.877679] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1525.916646] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1525.940773] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1525.964596] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.004697] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.020631] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.036451] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.052497] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.068404] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.092592] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.108313] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.164198] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.214721] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.236181] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.260008] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.276001] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.299951] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.323879] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.339743] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.411719] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.435739] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1526.452748] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1528.243589] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1530.543029] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1531.756489] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1531.849838] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1531.872950] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1531.912835] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1531.928756] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1531.947343] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1531.968678] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1531.992630] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1533.313514] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1534.391371] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1539.133987] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1546.663023] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1547.293654] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1547.437541] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1548.068360] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1549.162070] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1550.487673] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1554.240122] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1561.928863] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1561.941237] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1561.973164] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1561.998175] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.021113] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.037126] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.054630] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.068977] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.100867] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.116891] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.140819] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.164761] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.180740] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.204829] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.224022] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1562.236559] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.262072] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.292579] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.308477] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.324465] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.348917] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.404285] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1562.428231] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1563.865534] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1563.899186] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1563.929412] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1563.985146] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1564.001016] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1564.025062] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1564.049066] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1564.065857] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1564.105776] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1564.130717] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1564.154722] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1564.172284] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1564.194477] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1564.218553] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1564.240678] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1564.264666] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -32
[ 1564.523581] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1567.014900] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1567.078775] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1567.110582] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1567.421877] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1567.908888] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1569.952992] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1570.367871] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1571.158425] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1571.773139] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1572.467936] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1573.018769] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1573.146465] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1577.330156] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1578.128749] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1579.310367] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1579.996966] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1580.811122] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1580.843215] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1581.418179] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1581.769494] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1582.408086] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1583.198418] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71
[ 1583.972986] hid-generic 0003:046D:C047.0002: can't reset device, 0000:00:1d.0-1.1.1/input0, status -71


#uptime

> 19:43:55 up 27 min,  2 users,  load average: 0,03, 0,14, 0,45

#uname -a

> 
Linux merkabah 3.5.0-41-generic #64-Ubuntu SMP Wed Sep 11 15:40:48 UTC 2013 i686 i686 i686 GNU/Linux


#lsusb

> 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 002 Device 007: ID 050d:0237 Belkin Components F5U237 USB 2.0 7-Port Hub
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)


---

### Post by Kirboosy on 2013-10-03
So if you use a different mouse all together (different brand and model) it does the same thing everytime?

I've been googling for a cure and I have yet to find anything. Some people say reinstalls with different versions fix it or regular reinstalls of the same version fix it. Others report that they can't get it working no matter what they do. Its a really strange bug and not much information on it.

~Caboose

---

### Post by RaZoR1394 on 2013-10-05
We seem to have tracked it down to the USB hub. We are not having these problems anymore while the devices are connected directly to the computer USB ports. Our multifunctional printer also haves similar problems like the mice when connected to the hub.

The hub is a Belkin and I have ordered another one of another brand to replace it.

---

