# MP-SPDZ Algorithm Test

## Docker deployment

Requirements:

* docker
* docker-compose

```bash
cd docker
docker-compose -p mpc up -d
```

## Player data

`./Player-Data` folder, by default.

Stuff:

* Player private key
* Each player public keys
* Inputs
* Outputs
* ...

## Algorithms

Location:

* [./Programs]
* Source code: [./Programs/Source](./Programs/Source)
* Schedules: `./Programs/Schedules`
* Byte codes: `./Programs/Bytecode`

Documentation:

* [MP-SPDZ: High-Level Interface](https://mp-spdz.readthedocs.io/en/latest/Compiler.html)

## Algorithm compilation

```bash
N_PLAYERS=3
N_SAMPLES=4
docker exec -it node0.mpc ./compile.py test $N_PLAYERS $N_SAMPLES
```

## Algorithm execution

```bash
N_PLAYERS=3
N_SAMPLES=4
docker exec -it node0.mpc ./shamir-party.x 0 test-$N_PLAYERS-$N_SAMPLES -N $N_PLAYERS -ip ./Player-Data/hosts
```

```bash
N_PLAYERS=3
N_SAMPLES=4
docker exec -it node1.mpc ./shamir-party.x 1 test-$N_PLAYERS-$N_SAMPLES -N $N_PLAYERS -ip ./Player-Data/hosts
```

```bash
N_PLAYERS=3
N_SAMPLES=4
docker exec -it node2.mpc ./shamir-party.x 2 test-$N_PLAYERS-$N_SAMPLES -N $N_PLAYERS -ip ./Player-Data/hosts
```
