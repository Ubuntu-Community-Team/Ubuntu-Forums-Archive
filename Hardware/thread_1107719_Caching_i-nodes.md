---
title: "Caching i-nodes?"
date: 2009-03-27
forum: Hardware
---

### Post by darkzerox on 2009-03-27
I wrote a program that accesses every file on my system and collects a few stats about them. This program takes a few minutes to run the first time, and about a second to run the second time. I'm just curious to know why that is. I assume the i-nodes are getting cached somewhere along the line. My friend said they're probably getting cached by the hard drive (independently of the OS/file system), but that doesn't make sense to me. Does anyone have a better explanation?

I really don't think it's relevant, but I'm posting the source code here for your enjoyment.

```
#include <stdlib.h>
#include <dirent.h>
#include <stdio.h>
#include <string.h>
#include <errno.h>
#include <sys/stat.h>
#include <math.h>

const int nbins = 64, blksize = 4096, debug = 0;
unsigned nfiles = 0, frag[nbins], blocks[] = {0, 0, 0, 0};
double mean_fs, stddev_fs;
unsigned long long sum = 0, sq_sum = 0;

void getstats(const char *dirname);
void printstats();
int dec2pc(double x);
char* readable_fs(double size, char *buf);

int main(int argc, char** argv) {
    char startdir[80] = ".";

    if (argc > 1) {
        strcpy(startdir, argv[1]);
    }

    for (int i = 0; i < nbins; ++i) frag[i] = 0; // initialize bins

    getstats(startdir);

    mean_fs = sum / (double) nfiles;
    stddev_fs = sqrt(sq_sum / (double) nfiles - mean_fs * mean_fs);

    printf("\nFor directory %s\n\n", startdir);

    if (nfiles > 0) printstats();
    else printf("No files found.\n");

    return EXIT_SUCCESS;
}

void getstats(const char *dirname) {
    DIR *dp;
    struct dirent *ent;
    char path[1024];
    struct stat info;
    int unused_bytes, bin, nblocks;

    if ((dp = opendir(dirname)) == NULL) {
        if (debug) {
            printf("opendir(%s) failed: ", dirname);
            switch (errno) {
                case EACCES:
                    printf("Permission denied.\n");
                    break;
                case EMFILE:
                    printf("Too many file descriptors in use by process.\n");
                    break;
                case ENFILE:
                    printf("Too many files are currently open in the system.\n");
                    break;
                case ENOENT:
                    printf("Directory does not exist.\n");
                    break;
                case ENOMEM:
                    printf("Insufficient memory to complete the operation.\n");
                    break;
                case ENOTDIR:
                    printf("Not a directory.\n");
                    break;
                default:
                    printf("Unrecognized error code (%d).\n", errno);
                    break;
            }
        }
        return;
    }

    while ((ent = readdir(dp)) != NULL) {
        sprintf(path, "%s/%s", dirname, ent->d_name);
        lstat(path, &info);
        if (info.st_mode & S_IFDIR) {
            if (strcmp(ent->d_name, ".") == 0 || strcmp(ent->d_name, "..") == 0)
                continue;
            getstats(path);
        } else if (info.st_mode & S_IFREG) {
            nblocks = info.st_size / 4096;
            if (info.st_size % blksize != 0 || info.st_size == 0) nblocks++; // round up
            if (nblocks <= 10) {
                blocks[3]++;
                if (nblocks <= 4) {
                    blocks[2]++;
                    if (nblocks <= 2) {
                        blocks[1]++;
                        if (nblocks <= 1) {
                            blocks[0]++;
                        }
                    }
                }
            }
            unused_bytes = blksize - (info.st_size % blksize);
            bin = unused_bytes / nbins;
            if (bin < 0) bin = 0;
            else if (bin >= nbins) bin = nbins - 1;
            frag[bin]++;
            nfiles++;
            sum += info.st_size;
            sq_sum += info.st_size * info.st_size;
        }
    }

    closedir(dp);
}

void printstats() {
    char buf[32];

    // convert frag bins to percents
    for (int i = 0; i < nbins; ++i) {
        frag[i] = dec2pc(frag[i] / (double) nfiles);
    }

    // print internal fragmentation histogram
    for (int i = 30; i > 0; --i) {
        if (i % 5 == 0) printf(" %2d%% |", i);
        else printf("     |");
        for (int j = 0; j < nbins; ++j)
            if (frag[j] >= i) printf("*");
            else printf(" ");
        if (i % 5 == 0) printf("| %2d%%\n", i);
        else printf("|\n");
    }
    printf("     +---'`--'`--'`--'`--'`--'`--'`--'`--'`--'`--'`--'`--'`--'`--'`---+\n");
    printf("     0               1K              2K              3K              4K\n");
    printf("                           Internal Fragmentation\n\n\n");

    // print block stats
    printf("Percentage of files:  1 block or less = %2d%%\n", dec2pc(blocks[0] / (double) nfiles));
    printf("                     2 blocks or less = %2d%%\n", dec2pc(blocks[1] / (double) nfiles));
    printf("                     4 blocks or less = %2d%%\n", dec2pc(blocks[2] / (double) nfiles));
    printf("                    10 blocks or less = %2d%%\n\n", dec2pc(blocks[3] / (double) nfiles));

    // misc stats
    printf("Number of files:     %d\n", nfiles);
    printf("Mean file size:      %s\n", readable_fs(mean_fs, buf));
    printf("Standard deviation:  %s\n", readable_fs(stddev_fs, buf));
}

int dec2pc(double x) {
    return int(x * 100 + .5);
}

char* readable_fs(double size, char *buf) {
    int i = 0;
    const char* units[] = {"B", "kB", "MB", "GB", "TB", "PB", "EB", "ZB", "YB"};
    while (size / 1024 > 1) {
        size /= 1024;
        i++;
    }
    sprintf(buf, "%.*f %s", i, size, units[i]);
    return buf;
}
```

---

### Post by mcduck on 2009-03-27
Your friend could be right,a s all modern hard drives have built-in cache that they use to store recently accessed data.

Although it's even more likely that the data is cached by Ubuntu. Linux always tries to use all available RAM to speed up your system. All the RAM that is  not used by running applications is used as disk cache to avoid having to read the same data from hard disk again.

---

