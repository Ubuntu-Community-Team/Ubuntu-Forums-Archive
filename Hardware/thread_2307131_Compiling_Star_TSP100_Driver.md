---
title: "Compiling Star TSP100 Driver"
date: 2015-12-22
forum: Hardware
---

### Post by kara4 on 2015-12-22
Hi,

I am getting this warning during I compile the Star TSP100 Driver. 

```
mkdir bin
# compiling rastertostar filter
gcc -Wl,-rpath,/usr/lib -Wall -fPIC -O2  -o bin/rastertostar src/rastertostar.c -lcupsimage -lcups
src/rastertostar.c: In function ‘main’:
src/rastertostar.c:1626:5: warning: ‘cupsRasterReadHeader’ is deprecated (declared at /usr/include/cups/raster.h:370): Use cupsRasterReadHeader2 instead. [-Wdeprecated-declarations]
     while (CUPSRASTERREADHEADER(ras, &header))
     ^
# compiling rastertostarlm filter
gcc -Wl,-rpath,/usr/lib -Wall -fPIC -O2  -o bin/rastertostarlm src/rastertostarlm.c -lcupsimage -lcups
src/rastertostarlm.c: In function ‘main’:
src/rastertostarlm.c:1186:5: warning: ‘cupsRasterReadHeader’ is deprecated (declared at /usr/include/cups/raster.h:370): Use cupsRasterReadHeader2 instead. [-Wdeprecated-declarations]
     while (CUPSRASTERREADHEADER(ras, &header))
     ^
# gzip ppd file
gzip -c ppd/sp512.ppd >> bin/sp512.ppd.gz
# gzip ppd file
gzip -c ppd/sp542.ppd >> bin/sp542.ppd.gz
# gzip ppd file
gzip -c ppd/sp712.ppd >> bin/sp712.ppd.gz
# gzip ppd file
gzip -c ppd/sp742.ppd >> bin/sp742.ppd.gz
# gzip ppd file
gzip -c ppd/sp717.ppd >> bin/sp717.ppd.gz
# gzip ppd file
gzip -c ppd/sp747.ppd >> bin/sp747.ppd.gz
# gzip ppd file
gzip -c ppd/tsp113.ppd >> bin/tsp113.ppd.gz
# gzip ppd file
gzip -c ppd/tsp143.ppd >> bin/tsp143.ppd.gz
# gzip ppd file
gzip -c ppd/tsp113gt.ppd >> bin/tsp113gt.ppd.gz
# gzip ppd file
gzip -c ppd/tsp143gt.ppd >> bin/tsp143gt.ppd.gz
# gzip ppd file
gzip -c ppd/tsp651.ppd >> bin/tsp651.ppd.gz
# gzip ppd file
gzip -c ppd/tsp654.ppd >> bin/tsp654.ppd.gz
# gzip ppd file
gzip -c ppd/tsp700II.ppd >> bin/tsp700II.ppd.gz
# gzip ppd file
gzip -c ppd/tsp800II.ppd >> bin/tsp800II.ppd.gz
# gzip ppd file
gzip -c ppd/tsp828l.ppd >> bin/tsp828l.ppd.gz
# gzip ppd file
gzip -c ppd/tup542.ppd >> bin/tup542.ppd.gz
# gzip ppd file
gzip -c ppd/tup592.ppd >> bin/tup592.ppd.gz
# gzip ppd file
gzip -c ppd/tup942.ppd >> bin/tup942.ppd.gz
# gzip ppd file
gzip -c ppd/tup992.ppd >> bin/tup992.ppd.gz
# gzip ppd file
gzip -c ppd/tsp1000.ppd >> bin/tsp1000.ppd.gz
# gzip ppd file
gzip -c ppd/hsp7000r.ppd >> bin/hsp7000r.ppd.gz
# gzip ppd file
gzip -c ppd/hsp7000s.ppd >> bin/hsp7000s.ppd.gz
# gzip ppd file
gzip -c ppd/hsp7000v.ppd >> bin/hsp7000v.ppd.gz
# gzip ppd file
gzip -c ppd/fvp10.ppd >> bin/fvp10.ppd.gz
# create setup shell script
cp src/setup.sh bin/setup
chmod +x bin/setup
# packaging
mkdir install
cp bin/rastertostar install
cp bin/rastertostarlm install
cp bin/*.ppd.gz install
cp bin/setup install
```


I have found the line in rastertostar.c
```
while (CUPSRASTERREADHEADER(ras, &header))
```

Should I change this to 'CUPSRASTERREADHEADER' to 'cupsRasterReadHeader2' ?

---

### Post by Yellow Pasque on 2015-12-22
No. You would need to make other changes as well since the two functions are slightly different: [https://www.cups.org/documentation.php/doc-2.0/api-raster.html#cupsRasterReadHeader](https://www.cups.org/documentation.php/doc-2.0/api-raster.html#cupsRasterReadHeader)

---

### Post by kara4 on 2015-12-23
Thanks a lot!

Changing this lines was enough
```
typedef unsigned (*cupsRasterReadHeader_fndef)(cups_raster_t *r, cups_page_header2_t *h);
```

---

