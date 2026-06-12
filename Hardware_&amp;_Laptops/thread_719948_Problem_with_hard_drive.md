---
title: "Problem with hard drive"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by jackyyll on 2008-03-09
I currently have two hard drives in my system, 1 (sda) a 500GB SATA drive and one (hdb) 250GB IDE drive. The ladder will not and will not do anything at all really...

I checked dmesg for it, and i got losts "hdb: lost interrupt" and i'm not sure what that means.

Here is the complete "dmesg | grep hdb" output:

```

$ dmesg | grep hdb                                                                                                                         (03-09 19:23)
[   25.521872]     ide0: BM-DMA at 0xe700-0xe707, BIOS settings: hda:pio, hdb:DMA
[   26.160360] hdb: WDC WD2500JB-00GVA0, ATA DISK drive
[   35.152712] hdb: max request size: 512KiB
[   65.127466] hdb: lost interrupt
[   95.115377] hdb: lost interrupt
[  125.091291] hdb: lost interrupt
[  125.091323] hdb: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
[  155.067247] hdb: lost interrupt
[  155.067275] hdb: cache flushes supported
[  155.067322]  hdb:hdb: dma_intr: status=0xd0 { Busy }
[  155.067393] hdb: DMA disabled
[  165.107188] hdb: lost interrupt
[  195.079169] hdb: lost interrupt
[  225.050962] hdb: lost interrupt
[  255.024495] hdb: lost interrupt
[  284.999432] hdb: lost interrupt
[  314.989689] hdb: lost interrupt
[  344.961794] hdb: lost interrupt
[  374.953879] hdb: lost interrupt
[  374.954082]  hdb1
[  404.923919] hdb: lost interrupt
[  434.899081] hdb: lost interrupt
[  464.873945] hdb: lost interrupt
[  474.867613] hdb: lost interrupt
[  504.840292] hdb: lost interrupt
[  534.814109] hdb: lost interrupt
[  564.788373] hdb: lost interrupt
[  594.760104] hdb: lost interrupt
[  624.734683] hdb: lost interrupt
[  654.708938] hdb: lost interrupt
[  684.680247] hdb: lost interrupt
[  694.673465] hdb: lost interrupt
[  724.648575] hdb: lost interrupt
[  754.620091] hdb: lost interrupt
[  784.594492] hdb: lost interrupt
[  814.565749] hdb: lost interrupt
[  844.540910] hdb: lost interrupt
[  874.514406] hdb: lost interrupt
[  904.489010] hdb: lost interrupt
[  914.477060] hdb: lost interrupt
[  944.451155] hdb: lost interrupt
[  974.426524] hdb: lost interrupt
[ 1004.399110] hdb: lost interrupt
[ 1034.373886] hdb: lost interrupt
[ 1064.347913] hdb: lost interrupt
[ 1094.319691] hdb: lost interrupt
[ 1124.292789] hdb: lost interrupt
[ 1134.285006] hdb: lost interrupt
[ 1164.257161] hdb: lost interrupt
[ 1174.248525] hdb: lost interrupt
[ 1204.223181] hdb: lost interrupt
[ 1234.197255] hdb: lost interrupt
[ 1264.170666] hdb: lost interrupt
[ 1294.144688] hdb: lost interrupt
[ 1324.116330] hdb: lost interrupt
[ 1354.088482] hdb: lost interrupt
[ 1384.063807] hdb: lost interrupt
[ 1394.055902] hdb: lost interrupt
[ 1424.028188] hdb: lost interrupt
[ 1453.999693] hdb: lost interrupt
[ 1483.975208] hdb: lost interrupt
[ 1513.949963] hdb: lost interrupt
[ 1543.921877] hdb: lost interrupt
[ 1573.896560] hdb: lost interrupt
[ 1603.867077] hdb: lost interrupt
[ 1613.861077] hdb: lost interrupt
[ 1643.831866] hdb: lost interrupt
[ 1673.805911] hdb: lost interrupt
[ 1703.780185] hdb: lost interrupt
[ 1733.754605] hdb: lost interrupt
[ 1763.728693] hdb: lost interrupt
[ 1793.699043] hdb: lost interrupt
[ 1823.673076] hdb: lost interrupt
[ 1833.667103] hdb: lost interrupt
[ 1863.637430] hdb: lost interrupt
[ 1893.611240] hdb: lost interrupt
[ 1923.585157] hdb: lost interrupt
[ 1953.559911] hdb: lost interrupt
[ 1983.533676] hdb: lost interrupt
[ 2013.506853] hdb: lost interrupt
[ 2043.479845] hdb: lost interrupt
[ 2053.469387] hdb: lost interrupt
[ 2083.445942] hdb: lost interrupt
[ 2113.418291] hdb: lost interrupt
[ 2143.389821] hdb: lost interrupt
[ 2173.365768] hdb: lost interrupt
[ 2203.338255] hdb: lost interrupt
[ 2233.311126] hdb: lost interrupt
[ 2263.287114] hdb: lost interrupt
[ 2273.277686] hdb: lost interrupt
[ 2303.250172] hdb: lost interrupt
[ 2333.222171] hdb: lost interrupt
[ 2363.196742] hdb: lost interrupt
[ 2393.170543] hdb: lost interrupt
[ 2423.144062] hdb: lost interrupt
[ 2453.117693] hdb: lost interrupt
[ 2483.089747] hdb: lost interrupt
[ 2493.083108] hdb: lost interrupt
[ 2523.055006] hdb: lost interrupt
[ 2553.028031] hdb: lost interrupt
[ 2583.001088] hdb: lost interrupt
[ 2612.975181] hdb: lost interrupt
[ 2642.948643] hdb: lost interrupt
[ 2672.922274] hdb: lost interrupt
[ 2702.895391] hdb: lost interrupt
[ 2712.889027] hdb: lost interrupt
[ 2742.861838] hdb: lost interrupt
[ 2772.834922] hdb: lost interrupt
[ 2802.809776] hdb: lost interrupt
[ 2832.783493] hdb: lost interrupt
[ 2862.757096] hdb: lost interrupt
[ 2892.726651] hdb: lost interrupt
[ 2922.704047] hdb: lost interrupt
[ 2932.697747] hdb: lost interrupt
[ 2962.671707] hdb: lost interrupt
[ 2992.644916] hdb: lost interrupt
[ 3022.618339] hdb: lost interrupt
[ 3052.591640] hdb: lost interrupt
[ 3082.565051] hdb: lost interrupt
[ 3112.538228] hdb: lost interrupt
[ 3142.511910] hdb: lost interrupt
[ 3152.501666] hdb: lost interrupt
[ 3182.475101] hdb: lost interrupt
[ 3192.468725] hdb: lost interrupt
[ 3222.442269] hdb: lost interrupt
[ 3252.415697] hdb: lost interrupt
[ 3282.389419] hdb: lost interrupt
[ 3312.362567] hdb: lost interrupt
[ 3342.336126] hdb: lost interrupt
[ 3372.309255] hdb: lost interrupt
[ 3402.282361] hdb: lost interrupt
[ 3412.272227] hdb: lost interrupt
[ 3442.245883] hdb: lost interrupt
[ 3472.219002] hdb: lost interrupt
[ 3502.192645] hdb: lost interrupt
[ 3532.165912] hdb: lost interrupt
[ 3562.139120] hdb: lost interrupt
[ 3592.112659] hdb: lost interrupt
[ 3622.086054] hdb: lost interrupt
[ 3632.079811] hdb: lost interrupt
[ 3662.053173] hdb: lost interrupt
[ 3692.026613] hdb: lost interrupt
[ 3721.999797] hdb: lost interrupt
[ 3751.973459] hdb: lost interrupt
[ 3781.946684] hdb: lost interrupt
[ 3811.919868] hdb: lost interrupt
[ 3841.892985] hdb: lost interrupt
[ 3871.866199] hdb: lost interrupt
[ 3901.839883] hdb: lost interrupt
[ 3931.813363] hdb: lost interrupt
[ 3961.786220] hdb: lost interrupt
[ 3991.759644] hdb: lost interrupt
[ 4021.732976] hdb: lost interrupt
[ 4051.706447] hdb: lost interrupt
[ 4081.679536] hdb: lost interrupt
[ 4111.652811] hdb: lost interrupt
[ 4141.625892] hdb: lost interrupt
[ 4171.602985] hdb: lost interrupt
[ 4201.576232] hdb: lost interrupt
[ 4231.549848] hdb: lost interrupt
[ 4261.522934] hdb: lost interrupt
[ 4291.495975] hdb: lost interrupt
[ 4321.469023] hdb: lost interrupt
[ 4351.442713] hdb: lost interrupt
[ 4381.416101] hdb: lost interrupt
[ 4411.389285] hdb: lost interrupt
[ 4441.362478] hdb: lost interrupt
[ 4471.335575] hdb: lost interrupt
[ 4501.308978] hdb: lost interrupt
[ 4531.282242] hdb: lost interrupt
[ 4561.255422] hdb: lost interrupt
[ 4571.249119] hdb: lost interrupt
[ 4601.222303] hdb: lost interrupt
[ 4631.195480] hdb: lost interrupt
[ 4661.168923] hdb: lost interrupt
[ 4691.142152] hdb: lost interrupt
[ 4721.115477] hdb: lost interrupt
[ 4751.088730] hdb: lost interrupt
[ 4781.062010] hdb: lost interrupt
[ 4811.035075] hdb: lost interrupt
[ 4841.008526] hdb: lost interrupt
[ 4870.981837] hdb: lost interrupt
[ 4900.955031] hdb: lost interrupt
[ 4930.928011] hdb: lost interrupt
[ 4960.901590] hdb: lost interrupt
[ 4990.875125] hdb: lost interrupt
[ 5020.848333] hdb: lost interrupt
[ 5050.821238] hdb: lost interrupt
[ 5080.798594] hdb: lost interrupt
[ 5110.771763] hdb: lost interrupt
[ 5140.745209] hdb: lost interrupt
[ 5170.718394] hdb: lost interrupt
[ 5200.691890] hdb: lost interrupt
[ 5230.664859] hdb: lost interrupt
[ 5260.638070] hdb: lost interrupt
[ 5290.611844] hdb: lost interrupt
[ 5320.585196] hdb: lost interrupt
[ 5350.558532] hdb: lost interrupt
[ 5380.531430] hdb: lost interrupt
[ 5410.504574] hdb: lost interrupt
[ 5440.477997] hdb: lost interrupt
[ 5470.451357] hdb: lost interrupt
[ 5500.424386] hdb: lost interrupt
[ 5510.418329] hdb: lost interrupt
[ 5540.391346] hdb: lost interrupt
[ 5570.364548] hdb: lost interrupt
[ 5600.338192] hdb: lost interrupt
[ 5630.311584] hdb: lost interrupt
[ 5660.284748] hdb: lost interrupt
[ 5690.257886] hdb: lost interrupt
[ 5720.231221] hdb: lost interrupt
[ 5750.206193] hdb: lost interrupt
[ 5780.177397] hdb: lost interrupt
[ 5810.150880] hdb: lost interrupt
[ 5840.124573] hdb: lost interrupt
[ 5870.097587] hdb: lost interrupt
[ 5900.071189] hdb: lost interrupt
[ 5930.044573] hdb: lost interrupt
[ 5960.017876] hdb: lost interrupt
[ 5989.990941] hdb: lost interrupt
[ 6019.964002] hdb: lost interrupt
[ 6049.937589] hdb: lost interrupt
[ 6079.910940] hdb: lost interrupt
[ 6109.888033] hdb: lost interrupt
[ 6139.861201] hdb: lost interrupt
[ 6169.834541] hdb: lost interrupt
[ 6199.805074] hdb: lost interrupt
[ 6229.779215] hdb: lost interrupt
[ 6259.753052] hdb: lost interrupt
[ 6289.726460] hdb: lost interrupt
[ 6319.700157] hdb: lost interrupt
[ 6349.672860] hdb: lost interrupt
[ 6379.647988] hdb: lost interrupt
[ 6409.622637] hdb: lost interrupt
[ 6439.592542] hdb: lost interrupt
[ 6469.565918] hdb: lost interrupt
[ 6499.540729] hdb: lost interrupt
[ 6529.514525] hdb: lost interrupt
[ 6559.487752] hdb: lost interrupt
[ 6589.460741] hdb: lost interrupt
[ 6619.434058] hdb: lost interrupt
[ 6649.407266] hdb: lost interrupt
[ 6679.380932] hdb: lost interrupt
[ 6709.354149] hdb: lost interrupt
[ 6739.327648] hdb: lost interrupt
[ 6769.304626] hdb: lost interrupt
[ 6799.277913] hdb: lost interrupt
[ 6829.251202] hdb: lost interrupt
[ 6859.224625] hdb: lost interrupt
[ 6889.197841] hdb: lost interrupt
[ 6919.171058] hdb: lost interrupt
[ 6949.144146] hdb: lost interrupt
[ 6979.117522] hdb: lost interrupt
[ 7009.091113] hdb: lost interrupt
[ 7039.064294] hdb: lost interrupt
[ 7069.037432] hdb: lost interrupt
[ 7099.010766] hdb: lost interrupt
[ 7128.984249] hdb: lost interrupt
[ 7158.957640] hdb: lost interrupt
[ 7188.930808] hdb: lost interrupt
[ 7218.903946] hdb: lost interrupt
[ 7248.877114] hdb: lost interrupt
[ 7278.850258] hdb: lost interrupt
[ 7308.823681] hdb: lost interrupt
[ 7338.797025] hdb: lost interrupt
[ 7368.774157] hdb: lost interrupt
[ 7398.746895] hdb: lost interrupt
[ 7428.720232] hdb: lost interrupt
[ 7458.693619] hdb: lost interrupt
[ 7488.666779] hdb: lost interrupt
[ 7518.639765] hdb: lost interrupt
[ 7548.613076] hdb: lost interrupt
[ 7578.586276] hdb: lost interrupt
[ 7608.559496] hdb: lost interrupt
[ 7638.532784] hdb: lost interrupt
[ 7668.506264] hdb: lost interrupt
[ 7698.479211] hdb: lost interrupt
[ 7728.452258] hdb: lost interrupt
[ 7758.429531] hdb: lost interrupt
[ 7788.403054] hdb: lost interrupt
[ 7818.376607] hdb: lost interrupt
[ 7848.353669] hdb: lost interrupt
[ 7878.327004] hdb: lost interrupt
[ 7908.300368] hdb: lost interrupt
[ 7938.273783] hdb: lost interrupt
[ 7968.246955] hdb: lost interrupt
[ 7998.220299] hdb: lost interrupt
[ 8028.193387] hdb: lost interrupt
[ 8058.166763] hdb: lost interrupt
[ 8088.139875] hdb: lost interrupt
[ 8118.113019] hdb: lost interrupt
[ 8148.086343] hdb: lost interrupt
[ 8178.059548] hdb: lost interrupt
[ 8208.032498] hdb: lost interrupt
[ 8238.006005] hdb: lost interrupt
[ 8267.979476] hdb: lost interrupt
[ 8297.955280] hdb: lost interrupt
[ 8327.929536] hdb: lost interrupt
[ 8357.899823] hdb: lost interrupt
[ 8367.892611] hdb: lost interrupt
[ 8397.866949] hdb: lost interrupt
[ 8427.837337] hdb: lost interrupt
[ 8457.811524] hdb: lost interrupt
[ 8487.785829] hdb: lost interrupt
[ 8517.760102] hdb: lost interrupt
[ 8547.734469] hdb: lost interrupt
[ 8577.704825] hdb: lost interrupt
[ 8607.679139] hdb: lost interrupt
[ 8637.653222] hdb: lost interrupt
[ 8667.627352] hdb: lost interrupt
[ 8697.601642] hdb: lost interrupt
[ 8727.572149] hdb: lost interrupt
[ 8757.546610] hdb: lost interrupt
[ 8787.520979] hdb: lost interrupt
[ 8817.495134] hdb: lost interrupt
[ 8847.469297] hdb: lost interrupt
[ 8877.439646] hdb: lost interrupt
[ 8907.413904] hdb: lost interrupt
[ 8937.388084] hdb: lost interrupt
[ 8967.362260] hdb: lost interrupt
[ 8997.336463] hdb: lost interrupt
[ 9027.310748] hdb: lost interrupt
[ 9057.281232] hdb: lost interrupt
[ 9087.255468] hdb: lost interrupt
[ 9117.229566] hdb: lost interrupt
[ 9147.203689] hdb: lost interrupt
[ 9177.177843] hdb: lost interrupt
[ 9207.148184] hdb: lost interrupt
[ 9237.122585] hdb: lost interrupt
[ 9267.096812] hdb: lost interrupt
[ 9297.070830] hdb: lost interrupt
[ 9327.045240] hdb: lost interrupt
[ 9357.015493] hdb: lost interrupt
[ 9386.989830] hdb: lost interrupt
[ 9416.963961] hdb: lost interrupt
[ 9446.938085] hdb: lost interrupt
[ 9476.912350] hdb: lost interrupt
[ 9506.882691] hdb: lost interrupt
[ 9536.856917] hdb: lost interrupt
[ 9566.831088] hdb: lost interrupt
[ 9596.805146] hdb: lost interrupt
[ 9626.779340] hdb: lost interrupt
[ 9656.753705] hdb: lost interrupt
[ 9686.724062] hdb: lost interrupt
[ 9716.698233] hdb: lost interrupt
[ 9746.672419] hdb: lost interrupt
[ 9776.646477] hdb: lost interrupt
[ 9806.620751] hdb: lost interrupt
[ 9836.591068] hdb: lost interrupt
[ 9866.565254] hdb: lost interrupt
[ 9896.539338] hdb: lost interrupt
[ 9926.513405] hdb: lost interrupt
[ 9956.487646] hdb: lost interrupt
[ 9986.462096] hdb: lost interrupt
[10016.432372] hdb: lost interrupt
[10046.406575] hdb: lost interrupt
[10076.380694] hdb: lost interrupt
[10106.354919] hdb: lost interrupt
[10136.329337] hdb: lost interrupt
[10166.299574] hdb: lost interrupt
[10196.273776] hdb: lost interrupt
[10226.247899] hdb: lost interrupt
[10256.222101] hdb: lost interrupt
[10286.196367] hdb: lost interrupt
[10316.166768] hdb: lost interrupt
[10346.141033] hdb: lost interrupt
[10376.115211] hdb: lost interrupt
[10406.089274] hdb: lost interrupt
[10436.063596] hdb: lost interrupt
[10466.034033] hdb: lost interrupt
[10496.008282] hdb: lost interrupt
[10525.982556] hdb: lost interrupt
[10555.956719] hdb: lost interrupt
[10585.930842] hdb: lost interrupt
[10615.905180] hdb: lost interrupt
[10645.875521] hdb: lost interrupt
[10675.849666] hdb: lost interrupt
[10705.823773] hdb: lost interrupt
[10735.797960] hdb: lost interrupt
[10765.772424] hdb: lost interrupt
[10795.742877] hdb: lost interrupt
[10825.717151] hdb: lost interrupt
[10855.691281] hdb: lost interrupt
[10885.665507] hdb: lost interrupt
[10915.639677] hdb: lost interrupt
[10945.610129] hdb: lost interrupt
[10975.584275] hdb: lost interrupt
[11005.558382] hdb: lost interrupt
[11035.532442] hdb: lost interrupt
[11065.506882] hdb: lost interrupt
[11095.477216] hdb: lost interrupt
[11125.451426] hdb: lost interrupt
[11155.425528] hdb: lost interrupt
[11185.399587] hdb: lost interrupt
[11215.373781] hdb: lost interrupt
[11225.362525] hdb: lost interrupt
[11255.336958] hdb: lost interrupt
[11285.311138] hdb: lost interrupt
[11315.285252] hdb: lost interrupt
[11345.259350] hdb: lost interrupt
[11375.229683] hdb: lost interrupt
[11405.203982] hdb: lost interrupt
[11435.178335] hdb: lost interrupt
[11465.152513] hdb: lost interrupt

```



Any help is appreciated...

---

### Post by teaker1s on 2008-03-21
use fsck to check drive

download a copy of knoppix and also gparted live boot iso's with these you will be able to see any issues and possibly repair.

try google you may strike lucky

---

