This project shall help find out how to get jooq to use a custom enum, when that enum is used as an array in postgres.

Executing this script requires docker, it will automatically pull a postgres image and run migrations via flyway against it, then generate code via jooq.

Run `./gradlew build` to see the compilation eventually fail when trying to access the enum array from the example record.

```
> Task :compileJava FAILED
/Users/napster/42/jooq-postgres-enum-array-forced-type/src/main/java/org/example/db/Repository.java:22: error: incompatible types: Exampleenum[] cannot be converted to ExampleEnum[]
        ExampleEnum[] wrongEnumArray = record.getEnums();
                                                      ^
1 error

FAILURE: Build failed with an exception.
```

`Exampleenum` being the enum generated by jooq, `ExampleEnum` being our own enum.


Related issue: [https://github.com/jOOQ/jOOQ/issues/9523](https://github.com/jOOQ/jOOQ/issues/9523)
