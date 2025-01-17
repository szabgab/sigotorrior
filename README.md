# Sigotorrior

sigotorrior is a command-line task management utility especially for work.

---

## A Quick Demonstration

Let's see Sigotorrior in action.

ln Sigotorrior, tasks are reffered as 'sigo', and a sigo is classified into one of three states: ready, waiting, or completed.
A sigo is initially in the ready state.

```bash
$ task add "Write daily report"
Created sigo 1

$ task add "Reply XXX-123"
Created sigo 2

$ task add "Write unit tests for utils" --priority l
Created sigo 3

```

Now let's see the list.

```bash
$ sigo list

 id P description
 -- - ------------------
 1  M Write daily report
 2  M Reply XXX-123
 3  L Write unit tests for utils

```

Let's suppose the following.

* We wrote the daily report.
* We replied in XXX-123, but must wait for a response.
* We haven't written any unit tests yet.

```bash
$ sigo done 1
Completed sigo 'Write daily report'

$ sigo wait 2
Waiting sigo 2 'Reply XXX-123'

```

Then, the list and the waiting list would look like this.

```bash
$ sigo list

 id P description
 -- - --------------------------
 3  L Write unit tests for utils

$ sigo waiting

 id P description
 -- - -------------
 2  M Reply XXX-123

```

Those are the main features, the 'add', 'done', 'wait', 'list' and 'waiting' commands.

## Install

### Cargo

```bash
cargo install sigo
```

## Sub commands

* **sigo add \<description\>**: add the sigo
  * -p, --priority: set the priority
* **sigo modify \<id\>**: modify the sigo
  * **-t, --text**: modify the description
  * **-p, --priority**: modify the priority
* **sigo annotate \<id\> --text \<annotation\>**: annotate the sigo with the annotation
* **sigo wait \<id\>**: change the status of the sigo from ready to waiting
* **sigo back \<id\>**: change the status of the sigo from waiting to ready
* **sigo done \<id\>**: done the sigo
* **sigo list**: list ready tasks
* **sigo waiting**: list waiting tasks

## Author

satake_makoto

## License

Sigowarrior is released under the MIT license.
