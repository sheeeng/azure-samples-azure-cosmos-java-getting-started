---
page_type: sample
languages:
- java
products:
- azure
description: "Azure CosmosDB is a globally distributed multi-model database."
urlFragment: "azure-cosmos-java-getting-started"
---

# Developing a Java app using Azure Cosmos DB Java SDK

Azure Cosmos DB is a globally distributed multi-model database. One of the supported APIs is the SQL API, which provides a JSON document model with SQL querying and JavaScript procedural logic. The sample uses sync APIs. For async APIs sample, please refer to [example](https://github.com/Azure/azure-sdk-for-java/blob/feature/cosmos/v4/sdk/cosmos/azure-cosmos-examples/src/main/java/com/azure/cosmos/examples/BasicDemo.java).

## Getting Started

### Prerequisites

- Install [direnv](https://direnv.net/).

- Create `.envrc` file with the following similar content.

```shell
source_env ${HOME}

JAVA_HOME="/Library/Java/JavaVirtualMachines/jdk-20.jdk/Contents/Home"
PATH="${JAVA_HOME}/bin:${PATH}"
export PATH

export M2_HOME="${HOME}/Downloads/apache-maven-3.9.1"
PATH="${M2_HOME}/bin:${PATH}"
export PATH

URI='CHANGEME_AZURE_COSMOS_ACCOUNT_URI'
KEY='CHANGEME_AZURE_COSMOS_ACCOUNT_KEY'
```

- Run the following command.

```shell
mvn exec:java@sync -DACCOUNT_HOST=${URI} -DACCOUNT_KEY=${KEY}
```

- The solution still cannot run as it contains error.

```text
[com.azure.cosmos.sample.sync.SyncMain.main()] INFO SyncMain - Create database AzureSampleFamilyDB if not exists.
[cosmos-rntbd-nio-2-2] WARN com.azure.cosmos.implementation.directconnectivity.rntbd.RntbdClientChannelPool - channel acquisition failed due to
[cosmos-rntbd-nio-2-1] WARN com.azure.cosmos.implementation.directconnectivity.rntbd.RntbdClientChannelPool - channel acquisition failed due to
io.netty.channel.ConnectTimeoutException: connection timed out: cdb-ms-prod-westeurope1-fd58.documents.azure.com/13.69.66.21:11006
        at io.netty.channel.nio.AbstractNioChannel$AbstractNioUnsafe$1.run(AbstractNioChannel.java:261)
        at io.netty.util.concurrent.PromiseTask.runTask(PromiseTask.java:98)
        at io.netty.util.concurrent.ScheduledFutureTask.run(ScheduledFutureTask.java:153)
        at io.netty.util.concurrent.AbstractEventExecutor.runTask(AbstractEventExecutor.java:174)
        at io.netty.util.concurrent.AbstractEventExecutor.safeExecute(AbstractEventExecutor.java:167)
        at io.netty.util.concurrent.SingleThreadEventExecutor.runAllTasks(SingleThreadEventExecutor.java:470)
        at io.netty.channel.nio.NioEventLoop.run(NioEventLoop.java:569)
        at io.netty.util.concurrent.SingleThreadEventExecutor$4.run(SingleThreadEventExecutor.java:997)
        at io.netty.util.internal.ThreadExecutorMap$2.run(ThreadExecutorMap.java:74)
        at io.netty.util.concurrent.FastThreadLocalRunnable.run(FastThreadLocalRunnable.java:30)
        at java.base/java.lang.Thread.run(Thread.java:1623)
```

* Before you can run this sample, you must have the following prerequisites:

   * An active Azure account. If you don't have one, you can sign up for a [free account](https://azure.microsoft.com/free/). Alternatively, you can use the [Azure Cosmos DB Emulator](https://azure.microsoft.com/documentation/articles/documentdb-nosql-local-emulator) for this tutorial. As the emulator https certificate is self signed, you need to import its certificate to the java trusted certificate store as [explained here](https://docs.microsoft.com/azure/cosmos-db/local-emulator-export-ssl-certificates).

   * JDK 1.8+
   * Maven

### Quickstart

* First clone this repository using

```bash
git clone https://github.com/Azure-Samples/azure-cosmos-java-getting-started.git
```

* From a command prompt or shell, run the following command to compile and resolve dependencies.

```bash
cd azure-cosmos-java-getting-started
mvn clean package
```

* This demo has both sync and async modes.
* From a command prompt or shell, run the following command to run the SYNC application.

```bash
mvn exec:java@sync -DACCOUNT_HOST=YOUR_COSMOS_DB_HOSTNAME -DACCOUNT_KEY=YOUR_COSMOS_DB_MASTER_KEY
```

* From a command prompt or shell, run the following command to run the ASYNC application.

```bash
mvn exec:java@async -DACCOUNT_HOST=YOUR_COSMOS_DB_HOSTNAME -DACCOUNT_KEY=YOUR_COSMOS_DB_MASTER_KEY
```

## About the code

The code included in this sample is intended to get you quickly started with a Java application that connects to Azure Cosmos DB with the SQL API.

## More information

- [Azure Cosmos DB : Service introduction and SLA](https://docs.microsoft.com/azure/cosmos-db/sql-api-introduction)
- [Azure Cosmos DB : SQL API](https://docs.microsoft.com/en-us/azure/cosmos-db/sql-query-getting-started)
- [Java SDK Github for SQL API of Azure Cosmos DB](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/cosmos/azure-cosmos)
- [Java SDK JavaDoc for SQL API of Azure Cosmos DB](https://azuresdkdocs.blob.core.windows.net/$web/java/azure-cosmos/latest/index.html)

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
