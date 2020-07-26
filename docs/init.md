# Init project

## required files

- docker-compose.yml
- api/Dockerfile.dev
- api/wait-for-it.sh

## run docker

- Build docker image

```bash
docker-compose build --no-cache
```

- Run docker

```bash
docker-compose up
```

## create proj

- access to container

```bash
docker-compose exec api bash
```

- create project

```bash
cargo new [PROJECT_NAME] --bin
```

- move [PROJECT_NAME] to upper folder

- Now, add Rocket as a dependency in your Cargo.toml:

```toml
[dependencies]
rocket = "0.4.5"
```

- Modify src/main.rs so that it contains the code for the Rocket Hello, world! program, reproduced below:

```rs
#![feature(proc_macro_hygiene, decl_macro)]

#[macro_use] extern crate rocket;

#[get("/")]
fn index() -> &'static str {
    "Hello, world!"
}

fn main() {
    rocket::ignite().mount("/", routes![index]).launch();
}
```
