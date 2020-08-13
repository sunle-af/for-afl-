# Fuzzing Fuzzgoat with AFL++

## AFL

AFL - American Fuzzy Lop
Developed by - Michal Zalewski
For installing afl++
```
git clone ​ https://github.com/AFLplusplus/AFLplusplus.git
```
```
make
```
```
sudo make install
```
   
## What it Fuzzgoat?

A vulnerable C program that is used for testing fuzzer’s.

## Download the source of fuzzgoat with:
````
git clone ​ https://github.com/fuzzstati0n/fuzzgoat.git
````


## Building Fuzzgoat:
Go to the path of fuzzgoat and the build it with make.
 {in this case fuzzgoat is located at Desktop/fuzzing/fuzzgoat}
 

For output create a out folder.
`mkdir out`  

## Get Set Fuzz!!

```
afl-fuzz -i in -o out ./fuzzgoat @@
```
● -i in Input Directory
● -o out Output Directory
● ./fuzzgoat -Binary to fuzz
● @@ -Is used for marking location in the target’s command line
where the input file should be in placed


{The basic tests and checks before fuzzer start.}


## Fuzzing and analysing the crashes:

{3 cycles,total path,27 unique crashes were found}
Data under out{output} directory:
Data under crashes:


### .triage_crashes.sh:-

Using `.triage_crashes.sh` to analyse the crashes from the output
directory.
For this goto to the location where afl in installed
Then goto to experimental/crash_triage/
``` 
./triage_crashes.sh /root/Desktop/fuzzing/fuzzgoat/out/ root/Desktop/fuzzing/fuzzgoat/fuzzgoat 
```


### Running crashes directly:-

```
./fuzzgoat/out/crashes/id:000025,sig:11,src:000116,time:166949,op:arith8,
pos:37,val:-5
```
{id can be anything depending on which crash you want to analyse}


### Analysing crash via GDB:-

```
gdb ./fuzzgoat
```

`(gdb) run out/crashes/id:000025,sig:11,src:000116,time:166949,op:arith8,pos:37,val:5`
This is the cause for the segmentation fault.



