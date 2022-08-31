Do the following:
```
./autogen.sh
./configure --enable-all --enable-debug CFLAGS='-DWOLFSSL_CALLBACKS -fsanitize=address'
make -j4
./examples/server/server -p 5011 -x -d -v4
```
and run a test that should connect to a wolfssl server, for example:
```
cargo +nightly test --target x86_64-unknown-linux-gnu --bin tlspuffin -p tlspuffin --features fixed-port --lib tcp::tests::test_wolfssl_buffer_under_read_server -- --nocapture --exact
``